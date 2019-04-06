# pw


##### pw: user '<username>' disappeared during update
During pkg update/install this error appears.  
This might be due to /etc/passwd and /etc/master.passwd getting out of sync

To resync /etc/passwd and /etc/master.passwd
```
/usr/sbin/pwd_mkdb -p /etc/master.passwd
```

To safe edit /etc/passwd
```
vipw
```

https://unix.stackexchange.com/questions/32981/user-disappeared-during-update-error