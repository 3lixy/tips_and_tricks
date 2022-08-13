# GNU Bash

##### Print to stderr within function

(>&2 echo "Message")

##### Print to stdout within function

(>&1 echo "Message")

##### Shared ssh-agent (place in ~/.bashrc)
```
check-ssh-agent() {
    [ -S "$SSH_AUTH_SOCK" ] && { ssh-add -l >& /dev/null || [ $? -ne 2 ]; }
}

# make ~/.tmp if it does not exist
[ ! -d "~/.tmp" ] && mkdir "~/.tmp"

# attempt to connect to a running agent
check-ssh-agent || export SSH_AUTH_SOCK="$(< ~/.tmp/ssh-agent.env)"

# if agent.env data is invalid, start a new one
check-ssh-agent || {
    eval "$(ssh-agent -s)" > /dev/null
    echo "$SSH_AUTH_SOCK" > ~/.tmp/ssh-agent.env
}
```
##### Infinite Bash History
```
# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE="INFINITE"
# HISTFILESIZE=
HISTTIMEFORMAT="%d/%m/%y %T "
```

##### Vault SSH login
```
export ssh_key_path="$HOME/.ssh/"
export vault_signed_key_file="id_rsa-signed.pub"

function file_older_than_seconds {
	test $(find "$1" -name "$2" -mmin -$3)
	if [ $? -eq 1 ]; then
		echo "1"
    else
		echo "0"
	fi
}

function vr {
	vault write -field=signed_key ssh-client/sign/root valid_principals="<REPLACE-ME-WITH-COMMA-SERPERATED-USER-LIST>" public_key=@$HOME/.ssh/id_rsa.pub > $HOME/.ssh/id_rsa-signed.pub
}  

function refresh_vault_signed_key {

	if [ ! -f "$ssh_key_path/$vault_signed_key_file" ] || [ "$(file_older_than_seconds $ssh_key_path $vault_signed_key_file 170 )" == "1" ]; then
		vr
	fi
}
    
function vssh {
  if [ "$1" == "" ]; then
    vssh_usage
    return
  fi
  refresh_vault_signed_key
  ssh <REPLACE_WITH_USER>@"${1}" -i ~/.ssh/id_rsa-signed.pub
}

function vssh_usage {
  echo "usage:"
  echo ""
  echo "vssh <hostname|ip>"
  echo ""
  echo "e.g. vssh my-hostname" 
}

function vscp_usage {
  echo "usage:"
  echo ""
  echo "vscp pull|push source destination"
  echo ""
  echo "e.g. vscp push /my/local/path/to/file my-remote-host:/remote/path" 
  echo "e.g. vscp pull /my/local/path/to/file my-remote-host:/remote/path" 
}

function vscp {
  if [ "$1" == "" ] || [ "$2" == "" ] || [ "$3" == "" ]; then
    vscp_usage
    return
  fi
  refresh_vault_signed_key
  if [ "$1" == "pull" ]; then
    refresh_vault_signed_key
    scp -i ~/.ssh/id_rsa-signed.pub <REPLACE_WITH_USER>@"$3" "$2"
  elif [ "$1" == "push" ]; then
    refresh_vault_signed_key
    scp -i ~/.ssh/id_rsa-signed.pub "$2" <REPLACE_WITH_USER>@"$3"
  else
    vscp_usage
    return
  fi
}

export -f vssh
export -f vscp
export -f vr
export VAULT_ADDR='https://vault.example.com:8200'
```

##### PS1 Escaping
For reference here is the info on bash escaping: 
http://tldp.org/HOWTO/Bash-Prompt-HOWTO/bash-prompt-escape-sequences.html. 
If one was to use a script as PS1 you would need to use \001 and \002 instead of 
\\[ and \\] as detailed here: https://wiki.archlinux.org/index.php/Bash/Prompt_customization
