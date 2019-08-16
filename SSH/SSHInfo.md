Generate key:\
ssh-keygen -t rsa -C "lanqingzi@gmail.com"
```
Ssh config:

Host Azure-server
User mlan
HostName 13.91.92.102
IdentityFile ~/.ssh/id_rsa
```
Ssh with key\
Ssh -i id_rsa name@ip