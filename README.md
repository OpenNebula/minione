# miniONE

**miniONE** is an easy to use deployment tool to build an evaluation OpenNebula cloud based on either virtual machines (KVM), system containers (LXD), micro VMs (Firecracker) or Edge deployment on Packet. All necessary components to manage and run the virtual machines or containers are installed and configured on your dedicated system with just a single command run.

**Follow the detailed [tutorial](https://docs.opennebula.io/minione/)**.

## Requirements

Common min. requirements:
- 4 GiB RAM
- 20 GiB free space on disk
- default installation of the operating system with the latest updates
- privileged user access (`root`)
- openssh-server package installed

For **KVM evaluation** on a dedicated physical server for both the front-end and one KVM hypervisor node:
- physical host
- x86-64 Intel or AMD processor with **virt. capabilities**
- operating system:
  - CentOS 7 (RHEL 7) or CentOS 8 (RHEL 8)
  - Debian 9, 10
  - Ubuntu 16.04, 18.04, 20.04

For **LXD evaluation** on a dedicated physical server or virtual machine for both the front-end and one LXD hypervisor node:
- physical host or virtual machine (e.g., Amazon EC2 VM)
- x86-64 Intel or AMD processor
- operating system:
  - Ubuntu 18.04, 20.04

For **Firecracker evaluation** on a dedicated physical server or virtual machine for both the front-end and one Firecracker hypervisor node:
- physical host or virtual machine (e.g., Amazon EC2 VM)
- x86-64 Intel or AMD processor
- operating system:
  - CentOS 7 (RHEL 7) or CentOS 8 (RHEL 8)
  - Debian 9, 10
  - Ubuntu 16.04, 18.04, 20.04

For **Edge evaluation** on a dedicated physical server or virtual machine for the front-end and one remote Packet edge physical server for one **KVM or Firecracker** hypervisor node:

- physical host or virtual machine (e.g., Amazon EC2 VM)
- x86-64 Intel or AMD processor
- operating system:
  - CentOS 7 (RHEL 7) or CentOS 8 (RHEL 8)
  - Debian 9, 10
  - Ubuntu 16.04, 18.04, 20.04

## Quickstart

Download the [latest release](https://github.com/OpenNebula/minione/releases/latest) of the **miniONE** tool, run it and follow the instructions on the terminal.

### Get KVM cloud

Run the commands to deploy the evaluation cloud:

```
wget 'https://github.com/OpenNebula/minione/releases/latest/download/minione'
sudo bash minione
```

### Get LXD cloud

Run the commands to deploy the evaluation cloud:

```
wget 'https://github.com/OpenNebula/minione/releases/latest/download/minione'
sudo bash minione --lxd
```
### Get Firecracker cloud

Run the commands to deploy the evaluation cloud:

```
wget 'https://github.com/OpenNebula/minione/releases/latest/download/minione'
sudo bash minione --firecracker
```

### Get Edge cloud on Packet

miniONE will install OpenNebula frontend on the host where you run the command and also deploy and configure a hypervisor host on the Edge ([Packet](https://www.packet.com/) in this case) where you can spawn your VMs.

Run the commands to deploy the evaluation cloud:

```
wget 'https://github.com/OpenNebula/minione/releases/latest/download/minione'
sudo bash minione --edge packet --edge-packet-token [packet-token] --edge-packet-project [packet-project]
```

Optionally, you can use choose deploy to **Firecracker** hypervisor on the Edge.

```
wget 'https://github.com/OpenNebula/minione/releases/latest/download/minione'
sudo bash minione --firecracker --edge packet --edge-packet-token [packet-token] --edge-packet-project [packet-project]
```

## License

Copyright 2002-2020, OpenNebula Project, OpenNebula Systems (formerly C12G Labs)

Licensed under the Apache License, Version 2.0 (the "License"); you may
not use this file except in compliance with the License. You may obtain
a copy of the License at http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
