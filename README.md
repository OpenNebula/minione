# MiniONE

MiniONE is an easy to use deployment tool for the OpenNebula KVM evaluation environment. All necessary components to manage and (locally) run the virtual machines are installed and configured on your dedicated physical host with just a single command run.

## Requirements

- dedicated physical host supporting hardware virtualization
- min.  2 GiB RAM
- min. 20 GiB free space on disk
- operating system **CentOS 7, Ubuntu 16.04, or Ubuntu 18.04**
- fresh default install of the operating system with the latest updates
- privileged user access (`root`)

## Quickstart

Download the tool, run it and follow the instructions from the terminal:

```
sudo bash minione
```

If the deployment ends succesfully, you now have your OpenNebula all-in-one evaluation environment ready to use!

### Deployment Steps

- enable OpenNebula repository
- install OpenNebula frontend and KVM hypervisor
- prepare networking for virt. machines (bridge `minionebr`)
- configure firewall to provide NAT for virt. machines
- run private DNS server for virt. machines (`dnsmasq`)
- start OpenNebula and prepare user, virt. networks, datastores
- import CentOS 7 virtual machine appliance

## Advanced Deployment

The evaluation deployment tool comes with default parameters suitable for most cases. You can list all the deployment parameters by running:

```
sudo bash minione --help
```

### Examples

Start a verbose deployment and set own password for the default OpenNebula user:

```
sudo bash minione --verbose --password MySecretPassword
```

Specify OpenNebula virtual private network IP range for new deployment:

```
sudo bash minione --vnet-address 192.168.100.0 --vnet-gateway 192.168.100.1 --vnet-ar-ip-start 192.168.100.2
```
