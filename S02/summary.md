# Session 02

## Switch

### debugging information

show mac table
```
show mac-address-table
```

show running(current) config of switch

```
show running-config (show ru)
```

```
show vlan brief
```

```
show interface f0/1 switchport
```

```
show interfaces status
```

```
show vtp status
```

## VLAN 

### Trunk Link

when a link should pass traffic of different VLANs.

the `IEEE 802.1Q` is used. this one labels each packet with `tag` indicating to which VLAN this packet belonged.

### Access Link

just pass the specified VLAN packets (for example only VLAN 100)

### Commands

set link to trunk/access

```
switchport mode trunk/access
```

add description for each link

```
description something...
```

### Creating VLAN

```
conf t
vlan <number>
name <the name of the vlan>
exit
```

### Assign VLANs to Links (Access)

```
conf t
interface fa 0/18 (actually you should select interface(s) )
switchport mode access
switchport access vlan <num>
```

### Config Trunk

```
conf t
interface fa 0/1 (select interfaces)
switchport mode trunk
```

what the below command does is to change the native vlan of the current switch to vlan 99. by default it is vlan 1. the native vlan packets won't get taged (they are treated normally). so when a packet is from vlan 99 , it is untaged and sent. on the receiving side when such packet (untaged packet) is received it is assumed to be vlan 99 (if configured correctly) 

```
switchport trunk native vlan <num>
```

if you don't specify vlans, by defualt the traffic of all vlans are transmitted. 

> important note is that : when using this command be aware of `add` in it. when you use `add` the vlans are appended to the current list. however, when you don't use `add` the list gets overwrited (switchport trunk allowed vlan 10,20,30)
```
switchport trunk allowed vlan add 10,20,30
```

you should use this command if the link does not have any default protocol on trunk links. this command will set the protocol of the trunk link to `IEEE 802.1Q`.

```
switchport trunk encapsulation dot1q
```

### debugging trunk config

```
show interface f0/1 switchport
```




###  (Start-up) switch

#### Cleaning

```
write erase
delete flash:/vlan.dat
reload
```


shutdown the interfaces (ports)
```
conf t
interface range fastEthernet 0/1-24
shutdown
```

by default, when you enter anything that is not command it will look it up in a dns server. by entering this command you will disable it.

```
no ip domain-lookup
```

#### Assign IP to SVI

```
conf t
interface vlan <num>
ip address <ip> <subnet> (i.g. ip address 192.168.100.1 255.255.255.0)
```



### VTP (VLAN Trunking Protocol)

```
conf t
vtp mode transparent/client/server
```

#### config VTP domain
when using Server/Client, the configured VLANs are shared from Server to Clients. they should be in the same domain.

```
conf t
vtp domain <name>
```


set password for domain

```
vtp password <pass>
```





