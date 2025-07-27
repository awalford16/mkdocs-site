## ARP

Address Resolution Protocol is an protocol for discovering devices on the local network. A device will send a broadcast message out asking for a device with a particular IP address. This broadcast will reach every device on the layer 2 network. The device that has that IP address will respond to the ARP request with its MAC address.

ARP packets are sent when a device does not know how to reach another device on the same network. Once ARP is successful the device will no longer need to send ARP requests everytime it needs to route to that device, it knows the target MAC address and can route the reqeust accordingly.

Devices will then build ARP tables, keeping track of the MAC address of particular devices.

```
# Show MAC Address table on mac or linux
arp -a
```

## Gratuitous ARP

Gratuitous ARP works in the opposite direction to ARP. Instead of waiting for a device to ask for an IP address, a device broadcasts its IP address across the network.

## Broadcast

A broadcast message is a network packet send out to every device on the network. When it reaches a network device like a switch, the packet is sent out of every port in the same VLAN.

## Default Gateway

If a device receives a packet with an IP address which is not deemed to be on its local network, then the packet will be sent to the default gateway, which is typically the router on the network. The default gateway will have a routing table on how to route different IP address ranges.

## Layer 2

Layer 2 refers to networking communication happening within a VLAN where routing is based on MAC addresses.

Layer 2 devices build up MAC address tables based on ARP requests.

## Layer 3

Layer 3 refers to networking communication happening on the IP address level. Network packets will be encapsulated with packet headers specifying a source and destination IP. The destination IP is used to route the packet across the internet.

Routers on the internet will build routing tables based on their knowledge of what the next hop should be based on a particular IP range.

## OSI Model

The OSI model refers to the different layers traversed by data between 2 devices. It starts at layer 7, works its way down to the physical networking media between devices. At the end device, it works its way back up to the application layer.

1. Pyhsical
2. Data Link Layer (MAC Address information)
3. Network Layer (IP Address information)
4. Transport Layer (Protocols)
5. Session Layer (Port information)
6. Presentation Layer
7. Application Layer

## VLAN

A VLAN is a segmentation of a layer 2 network. VLANs can be used to reduce broadcast domains and segment the network so only particular devices can communicate with one another. Devices in one VLAN will not receive layer 2 broadcast messages from another VLAN.

## VXLAN

VXLAN is a type of overlay network which allows for 2 virtual machines on difference physical hosts which are in different networks, to communicate over layer 2 as if they are in the same network.

VXLAN uses a virtual switch on the physical host to encapsulate the packet with the layer 3 information of the target physical host. The virtual switch needs to build a routing table which maps the MAC addresses of virtual machines to their physical host IP. One way of gatering this information is by being part of a multicast group which allows them to receive ARP packets containing virtual machine information from other hosts.
