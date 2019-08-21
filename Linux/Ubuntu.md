Use the usermod command to add the user to the sudo group  
`usermod -aG sudo username`  

start, stop or restart mysql process  
`systemctl start mysqld`  
`systemctl stop mysqld`  
`systemctl restart mysqld`  

enable or disable mysql process when reboot  
`systemctl enable mysqld`  
`systemctl disable mysqld`  

check status of mysqld  
`systemctl status mysqld`  

check all status  
`systemctl list-units`  
