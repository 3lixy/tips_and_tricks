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

##### PS1 Escaping
For reference here is the info on bash escaping: 
http://tldp.org/HOWTO/Bash-Prompt-HOWTO/bash-prompt-escape-sequences.html. 
If one was to use a script as PS1 you would need to use \001 and \002 instead of 
\\[ and \\] as detailed here: https://wiki.archlinux.org/index.php/Bash/Prompt_customization
