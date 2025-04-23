# Session 01

## why network

easier, safer, faster and cheaper transfer your data (file, video, document, ...)

## Different Network Types

- LAN (Local Area Network)
- MAN (Metropolitan Area Netwrok) ? what is this actually ?
- WAN (Wide Area Netwrok)
- SAN (Storage Area Network) ? what is this ?
- PAN (Personal Area Network) ? what about this ?
- CAN (Campus Area Network) ? what about this ?

## Types of Network Service 

- server-client
- peer-to-peer

## Data Transfer Technology

- Broadcast
    - there is a common communication channel between clients and each packet is received by each and every client, but the packet is processed only by the client whose address is specified on the packet ( is this safe ? can't others sniff ? )
- Point to Point
    - okay lets connect two hosts directly
- NBMA (Non-Broadcast Multi-Access)
    - I just know that each packet is not sent to every host on the network and it is usually used in WAN
    - need more info on what this NBMA is ?

## Types of Physical Connection in LAN
__remember__ : provide some images later

- bus
- star
- ring
- mesh
- hybrid

## OSI (open system interconnection)

- Physical Layer 
    - should transfer bits correctly (completely communication theory)
- Data-Link Layer
    -  breaks data to smaller chunks called `frame`
    - tries to prevent possible faults on the physical communication link
    - provide service to `Network` Layer
- Network Layer
    - this layer handle addressing and routing of packets
- Transport Layer
    - creates a logical process to process connection between two hosts
- Session Layer
    - it creates a session between source and destination application/host
    - this layer is responsible for synchronization of both ends
    - some examples : 
        - authentication of both ends
        - checking packet validity
        - termination of session

- Presentation Layer
    - it acts as a translator for application layer
    - some activities : 
        - formating
        - compression
        - encryption
- Application Layer
    - you know better than me what we do here !

## IP (internet protocol)

### intro

- logical addressing.
- introduced in early 1980s
- consists of 4 bytes (255.255.255.255) in other word 32 bits
- supports up to 2^32 distinct devices
    - it was enough for the time of invention. but is overwhelmed now (emergence of NAT)
- no built-in security
- complex header

### IPv6

- each address i 128 bits long
- contains built-in security (IPsec) ? what is this ?
- efficient and lighter header (compared to IPv4)

### classes of IPv4

| subnet mask   | CIDR | start   | end             | bit pattern |  class  |
| ------------- | ---- | --------- | --------------- | ----------- | ------- |
| 255.0.0.0     | /8   | 0.0.0.0   | 127.255.255.255 | 0           | Class A |
| 255.255.0.0   | /16  | 128.0.0.0 | 191.255.255.255 | 10          | Class B |
| 255.255.255.0 | /24  | 192.0.0.0 | 223.255.255.255 | 110         | Class C |
| Not Defined   | /4   | 224.0.0.0 | 239.255.255.255 | 1110        | Class D (multicast)|
| Not Defined   | /4   | 240.0.0.0 | 255.255.255.255 | 11110       | Class E (Reserved) |
 

