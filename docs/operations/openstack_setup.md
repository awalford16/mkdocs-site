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
