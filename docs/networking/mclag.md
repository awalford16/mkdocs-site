# What is MCLAG?

Link aggregation provides load balancing across two physical links between 2 devices.

Multi-Chassis Link Aggregation Groups allow for a single leaf switch to be connected to two spine switches via a single LAG connection.

This eliminates the need for Spanning Tree protocol to block ports and make use of all connections between switches.

The approach is also very scalable, since new spine switches can be added to existing LAGs.

#How to configure MCLAG

The commands below are for Dell SONiC switches.

## Create a LAG

Firstly, a LAG needs to be setup on each of the switches

```
interface PortChannel X
switchport trunk allowed vlan $VLAN_ID
```

## Create an MCLAG Domain

For each member of the MCLAG, they need to be registered to the MCLAG domain. A switch can only support one MCLAG domain.

```
mclag domain $ID
peer-link $INTERFACE
```

The peer link refers to the interface port or port channel which links the spine switches.

A keepalive link connects MCLAG peer switches to carry out periodic heatbeat messages. This should be configured on each of the peer switches (e.g. spine switches) used.

```
source-ip $PEER1_IP
peer-ip $PEER2-IP
```

Finally, the port channel interface needs to be added to the MCLAG

```
interface PortChannel X
mclag $ID
```
