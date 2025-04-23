# Session 03

## Inter-VLAN Routing

### Setup

by using this command you will enable processing at layer-3 (Network layer)
```
conf t
ip routing
```

you should define a SVI for each vlan you want to have layer-3 routing
```
conf t
interface vlan <num>
```

assign ip address to each SVI and enable it (using `no shutdown`)

```
conf t
interface vlan <num>
ip address <ip> <subnet> (i.g. ip address 192.168.99.1 255.255.255.0)
no shutdown
```


## EtherChannel

### Setup

choose the range of interfaces that are to be grouped together.

```
conf t
interface range fa 0/1-4
```

set the protocol

```
channel-protocol pagp/lacp
```

create the channel group

```
channel-group <num> mode desirable/auto/...
```

### Config Channel group

you can select your channel group and apply desired confi

```
interface port-channel <num>
```


### Debug

```
show etherchannel summary

show etherchannel <num> port-channel
```


## DHCP

### Setup
ensure that DCHP service is enabled on switch layer-3
```
service dhcp
```

create an ip pool for each vlan 

```
ip dhcp pool <name> (i.g. ip dhcp pool VLAN10_POOL)
```

config each pool

```
ip dhcp pool <name>
network <ip> <subnet>
default-router 192.168.10.1 (SVI IP of VLAN 10)
dns-server <primary_ip> <secondary_ip>
lease 7
```


### Debug

```
show ip dhcp binding (show leased IPs)
show ip dhcp pool (checks pool usage)
```
