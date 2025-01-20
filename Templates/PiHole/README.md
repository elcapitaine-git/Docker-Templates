# Pi Hole Server


## Critical Informations

You will need to disable the DNS Stub Listener

# Steps 
1. sudo nano /etc/systemd/resolved.conf
2. Change : DNSStubListener=no
3. sudo service systemd-resolved restart