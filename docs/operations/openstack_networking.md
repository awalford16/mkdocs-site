## Networking Options

Openstack provides 2 options for networking.

### Provider Networks
Openstack bridges virtual networks to physical networks and relies on physical network infrastructure for layer 3 routing. A DHCP service provides IP address information to instances.

This option lacks support for self-service networks as well as LBaaS and FWaaS

### Self-service Networks

Self-service networks use segmentation methods such as VXLAN and routes virtual networks to physical networks using NAT.

Using the benefits and dynamic approach of VXLAN, users can create their own virtual networks without needing to rely on changes to the underlying physical network.

## Open VSwitch

When deploying Openstack with Kolla, each host will get an `openvswitch-vswitchd` container deployed. This is responsible for running OpenVSwitch and handling bridge networking across the virtual machines deployed on the host.
