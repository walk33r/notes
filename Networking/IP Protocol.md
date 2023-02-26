

[IP Protocol](https://www.rfc-editor.org/rfc/rfc791)

IP packet is a bunch of data attached from above layers + meta_data. 

![[ip_protocol.png]]

Why we need IP Address even though we have mac-address ? 
- scaling issue (mac addresss is tied to hardware device which is very random, we don't have any kind of routing information decide whether to deliver frame or not. )
- arp protocol works in a way that it sends data/frame to all devices connected to network which can be a huge problem security wise and scaling issue.
- address is random does not contain information of where to send the frame and where not to

Meta data includes
- Source Ip Address
- Destination Ip Address
- Total length (16 bit ~ 65536 byte) => This contains the size of the whole thing ip packet which include ip packet header + data size. MTU (Maximum Transmission Unit) in case of ethernet is generally 1500 Byte that means we can transfer 1500 bytes of data in single frame. if total length of ip packet  is greater than MTU than we need to fragment the ip packet. in case of let's say a ip packet of 2000 byte total length will get fragmented into 2 frames of size 1500 and 500 byte respectively. fragmentation is not generally used as the cost associated with it for the reassembly of ip packet at host. 
- and much more...


**Size of IPv4 is 4 bytes (32 bits)**

Size of IP header itself is 20 byte. (4 byte in each row) at max it can be 60 bytes if certain options are enable.

a.b.c.d/x (a.b.c.d) are 8 bit octets represented in decimal notation) and x is the number of bits alloted to network.

For eg : 192.168.1.12/24 means that 24 bits are alloted to network therefore the subnet mask would be 
255.255.255.0 . First 3 octets are alloted to network and last octet are alloted to host.

so we can have 2^24 networks with 255 host each starting with

192.168.1.0 (network address)
192.168.1.1 (host address)
192.168.1.1 (host address)
...
...
192.168.1.255 (broadcast address)


If a machine needs to send an ip packet to a particular destination ip-address, it checks first whether the destination ip-address is within the same subnet by comparing the network-address
of both source and destination ip-address.

for eg :

client (192.168.1.12) needs to send an ip-packet to (192.168.2.33)

we know the subnet mask of client is 255.255.255.0

binary form of ip-address(192.168.1.12)            =     11000000.10101000.00000001.00001100
binary form of subnet-mask(255.255.255.0)    =    11111111.11111111.11111111.00000000

performing bit-wise & operation of client ip-address with subnet-mask we get

11000000.10101000.00000001.00000000 => 192.168.1.0 is network address

performing same operation on destination ip address we get 192.168.2.0 as network address.

clearly both network address differs. 

therefore we can conclude that the IP packet we are trying to send to destination  does not reside on same network.


netstat -nr => command to show the routing table of a machine

arp poisoning ?
tcp blackhole ?

