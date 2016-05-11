# PowerDNS
powerDNS poc conf for internal addresses

This has been done on Ubuntu 14.04, you will need to install powerdns, and if you want a local recursor then also pdns-recursor. This works in a hybrid backend mode, this is using Bind backend and SQLite for DNSSEC. In order to get this ready on Ubuntu:
```bash
# sudo apt-get update
# sudo apt-get install pdns-server pdns-recursor
# sudo mkdir -p /etc/powerdns/bind
# sudo pdnssec create-bind-db /etc/powerdns/bind/dnssec.db
```
Make sure you do the above after configuring and restarting pdns service
```bash
# sudo update-rc.d pdns defaults
# sudo service pdns restart
```
Make sure you set up your DHCP server to point to this machine (with powerdns), or just modify resolvconf like this: (192.168.122.151 is the IP of this powerdns machine)
```bash
# sudo vim /etc/resolvconf/resolv.conf.d/head
### search mycomapny.local
### nameserver 192.168.122.151
# sudo resolvconf -u
```

