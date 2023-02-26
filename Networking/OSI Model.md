


![[osi_model.png]]




![[transmission.png]]


Terminology on each layer
- Frames on Layer 2
- Packet on Layer 3
- Segments on Layer 4 (if transport protocol is TCP)
- Datagram on Layer 4 (if transport protocol is UDP)

**Frame size (MTU) IP packet should better fit in a frame. We cannot put an IP Packet into multiple frames.**



metadata added by layer 2,3 and 4 are not-encrypted.


difference b/w hub and switch
layer 4 proxy (port forwarding is a special case of layer 4 proxying)
layer 4 load balancer
layer 7 proxy
layer 7 load balancer
cdn's


vpn works basically works at layer 3 protocol

is it possible for a frame to be rejected at the data link layer if the destination MAC address is not matched, even if the destination IP address of the device is correct or the other way around that frame is matched



router is a device which can work in 3 different layer
- layer 2 => act as a switch
- layer 3 => for routing basically
- layer 4 => to do NAT
