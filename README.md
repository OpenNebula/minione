# MiniONE

MiniONE is an easy to use deployment tool for the OpenNebula KVM evaluation environment. All necessary components to manage and (locally) run the virtual machines are installed and configured on your dedicated physical host with just a single command run.

## Requirements

- dedicated physical host supporting hardware virtualization
- min.  2 GiB RAM
- min. 20 GiB free space on disk
- operating system **CentOS 7, Ubuntu 16.04, Ubuntu 18.04, Ubuntu 18.10 or Debian 9**
- fresh default install of the operating system with the latest updates
- privileged user access (`root`)

## Quickstart

Download the [latest release](https://github.com/OpenNebula/minione/releases/latest) of the `minione` script, run it and follow the instructions from the terminal:

```
sudo bash minione
```

If the deployment ends succesfully, you now have your OpenNebula all-in-one evaluation environment ready to use! On the terminal, you'll see a deployment report with login information.

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

## License

Copyright 2002-2019, OpenNebula Project, OpenNebula Systems (formerly C12G Labs)

Licensed under the Apache License, Version 2.0 (the "License"); you may
not use this file except in compliance with the License. You may obtain
a copy of the License at http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
