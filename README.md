# miniONE

**miniONE** is an easy to use deployment tool to build an evaluation OpenNebula cloud based on either virtual machines (KVM) or system containers (LXD). All necessary components to manage and run the virtual machines or containers are installed and configured on your dedicated system with just a single command run.

## Requirements

Common min. requirements:
- 4 GiB RAM
- 20 GiB free space on disk
- default installation of the operating system with the latest updates
- privileged user access (`root`)

For KVM evaluation:
- physical host
- x86-64 Intel or AMD processor with **virt. capabilities**
- operating system:
  - CentOS 7 (RHEL 7)
  - Debian 9
  - Ubuntu 16.04, 18.04

For LXD evaluation:
- physical host or virtual machine (e.g., Amazon EC2 VM)
- x86-64 Intel or AMD processor
- operating system:
  - Ubuntu 18.04

For Edge (Packet) evaluation, for the frontend:
- physical host or virtual machine (e.g., Amazon EC2 VM)
- x86-64 Intel or AMD processor
- operating system:
  - CentOS 7 (RHEL 7)
  - Debian 9
  - Ubuntu 16.04, 18.04

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

### Get Edge cloud on Packet

Run the commands to deploy the evaluation cloud:

```
wget 'https://github.com/OpenNebula/minione/releases/latest/download/minione'
sudo bash minione --edge packet --edge-packet-token [packet-token] --edge-packet-project [packet-project]
```

MiniONE will install OpenNebula frontend on the host where you run the command and also configure one host one the Edge (Packet in this case) where you can spawn your VMs.

## Tutorial

Continue with detailed **[tutorial](https://github.com/OpenNebula/minione/wiki)**.

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
