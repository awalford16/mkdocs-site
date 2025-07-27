Openstack can be deployed in a number of ways. A popular tool for deployment is Kayobe which deploys the Openstack services to machines as docker containers.

Kayobe uses kolla-ansible to automate the deployment of Openstack services.

## Kayobe

```
# Configure Seed hypervisor
kayobe seed hypervisor host configure

# Configure a Seed host
kayobe seed host configure

# Configure an overcloud host
kayobe overcloud host configure
```

Kayobe has global configuration for each of these type of hosts under $KAYOBE_CONFIG_PATH. The configuration files names represent the host type.

```
seed.yml
controller.yml
compute.yml
```

## Service Deployment

With the Kayobe host configured, the services can be deployed.

```
# Deploy services for seed host
kayobe seed service deploy

# Deploy services for overcloud hosts
kayobe overcloud service deploy
```
