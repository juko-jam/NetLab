

### how to find system ip address and gateway 

1. go to network section of control panel in windows ( ncpl )
2. ip a (linux)
3. ifconfig (linux)
4. ipconfig (windows)

### how to share a file using smaba

#### in linux

1. sudo apt install samba
2. edit the /etc/samba/smb.conf file
3. add a new sharable section to the end of this file with following attributes
```
[share_section]
    comment = some comment
    path = /path/to/your/share
    read only = yes/no
    browsable = yes/no
```

4. allow the samba traffic by
```
sudo ufw allow samba
```

5. add a samba password for system user (or folder user)
```
sudo sambapasswd -a <username>
```

***note***:  the samba user is actually a unix user, but because the samba does not use the same password for its authentication you should manually add a new record for users of your linux in samba

#### in windows

to be added ...

### how to show arp table

arp -n
or 
arp -a

### manual name and address resolution

- nslookup \<ip address\>
- nslookup \<domain\>


### how to assign static ip to your interface (host)

to be added ...

### how to request a new ip from your DHCP : 

#### linux

sudo dhclient \<interface\>

```
sudo dhclient eth0
```

### how to request a DNS server from DHCP : 

to be added ...

### how to use hping3

to be added ...


### investigating your routing table (forwarding table) 

- show routing table :

1. route
2. netstat -r

### how to change your routing table

#### change your default gateway

1. remove your current gateway
```
sudo route delete default
```
2. add a new gateway

```
sudo route add default gw <ip>
```

#### how to block an ip

```
sudo route add <ip> reject
```

### how to store network traffic using tcpdump

```
sudo tcpdump -w capture.pcap
```


