## OpenStack Hardware

Openstack is built up of multiple hareware components. The core components are the controller and compute nodes. Optional additional hardware include a block and object storage node.

### Controller

The controller is responsible for running identity services, image services, placement services and management portions of compute, networking and agents.

It can optionally run portions of the block storage, objects storage and orchestration.

### Compute

Compute nodes run the hypervisor portaion that operates instances using the KVM hypervisor.

Additionally, it runs a networking service agent that connects instances to VNets and provides firewalling services to instances via security groups.

### Block storage

This node contains the disks

Traffic between this node and compute nodes uses the management network. It is recommended for production setups to have a dedicated storage network to increase performance and security.

## OpenStack services

### Nova

Nova is the service for handling Virtual machines on hosts. Under the hood it uses KVM (`virsh`), a linux hypervisor built into a kernel module. So from a host running Nova, you can run `virsh list` to view the active VMs on that host.

### Ironic

Ironic is the service which manages the baremetal hosts within Openstack. New baremetal hosts are registered with the Ironic service.

Ironic keeps track of the state of the host. See this diagram for more details: https://docs.openstack.org/ironic/latest/_images/states.svg. Detail of the states is also provided in [Openstack Ironic States](./openstack_ironic_states.md)

You can manage baremetal nodes in Ironic with the `openstack baremetal node` CLI, which allows for a host to be transitioned through different states and be put into maintenance mode.

Once a host is managed by Ironic, it will be viewable by the openstack admin using the command below:

```
openstack baremetal node list
```
