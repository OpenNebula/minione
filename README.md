# MiniONE

MiniONE is an easy to use deployment tool for the OpenNebula which setup either **KVM** or **LXD** (Linux containers) based evaluation environment. All necessary components to manage and run the virtual machines or containers are installed and configured on your dedicated machine with just a single command run.

## Requirements

- for **KVM** evaluation:
  - dedicated physical host
  - operating system: **CentOS 7, Ubuntu 16.04, Ubuntu 18.04, Ubuntu 18.10 or Debian 9**
- for **LXD** evaluation:
  - dedicated virtual machine or physical host
  - operating system: **Ubuntu 18.04, Ubuntu 18.10**
- min.  2 GiB RAM
- min. 20 GiB free space on disk
- fresh default installation of the operating system with the latest updates
- privileged user access (`root`)

## Quickstart

Download the [latest release](https://github.com/OpenNebula/minione/releases/latest) of the `minione` script, run it and follow the instructions on the terminal.

### KVM evaluation

Run:

```
sudo bash minione
```

### LXD evaluation

Run:

```
sudo bash minione --lxd
```

If the deployment ends succesfully, you now have your OpenNebula all-in-one evaluation environment ready to use! On the terminal, you'll see a deployment report with login information.

You can easily deploy a LXD/OpenNebula environment of a VM running on AWS. The minimal recommended instance type is perhaps t2.medium. Just give it at least 25GB disk space and allow access to the 9869 TCP where the WebUI is running.

### Deployment Steps

- enable OpenNebula repository
- install OpenNebula frontend and KVM or LXD hypervisor
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

Start a verbose deployment and setup LXD envirnoment instead of KVM:
```
sudo bash minione --verbose --lxd
```

Start a verbose deployment and set own password for the default OpenNebula user:

```
sudo bash minione --verbose --password MySecretPassword
```


Specify OpenNebula virtual private network IP range for new deployment:

```
sudo bash minione --vnet-address 192.168.100.0 --vnet-gateway 192.168.100.1 --vnet-ar-ip-start 192.168.100.2
```

## Try Out

### Report
Once the minione is done, you will get an overview how to connect to the web interface similar to following:

```
### Report
OpenNebula 5.8 was installed
Sunstone (the webui) is runninng on:
  http://192.168.100.101:9869/
Use following to login:
  user: oneadmin
  password: o6ARsMAdGe
```

### Try the Admin View in the Sunstone GUI

After the minione finishes, the first thing we are going to do is to log in as oneadmin to take a look at the Admin View of Sunstone, which has more options than the other Sunstone views for a regular users.

Take a look at all the already bootstrapped resources in the Sandbox.

![dashboard](https://raw.githubusercontent.com/OpenNebula/minione/master/screenshots/dashboard.png)


### Try the Cloud View

With the Admin View you can do anything in OpenNebula, but you don’t want all those options for the final users! Switch to the Cloud View to see how a final user will see OpenNebula:

![switch_to_cloud_view.png](https://raw.githubusercontent.com/OpenNebula/minione/master/screenshots/switch_to_cloud_view.png)

The Cloud View interface is much simpler and targeted at end users.

Create a new Virtual Machine by clicking the `+` button. Select the only available template and click `Create`.

After clicking create you will be taken to the dashboard where you can see your running VMs.

![vm_list](https://raw.githubusercontent.com/OpenNebula/minione/master/screenshots/vm_list.png)

You can click on your VM and manage it: access it through VNC, Save its state, Reboot it, etc:

![vm_info](https://raw.githubusercontent.com/OpenNebula/minione/master/screenshots/vm_info.png)

Clicking on the Console icon will let you login into the VM. The default credentials are:

Login: root
Password: opennebula

With the oneadmin role you can customize what your cloud users can do and see.


### Quick Overview of the CLI Interface

You need to connect to the sever either using the web console or using ssh. OpenNebula runs as the oneadmin user, and the main administrator should run commands as that user, therefore the first thing you need to do is to switch to oneadmin:

```
su - oneadmin
```

From the oneadmin account you can see all the already bootstrapped resources:
```
onehost list
```

There is one network created
```
$ onevnet list
```

You can see the leases and the specific configuration of the network
```
$ onevnet show 0
```

A Centos image has been created
```
$ oneimage list
```

A Virtual Machine template is registered
```
$ onetemplate list
```

You can see the template configuration if further detail
```
$ onetemplate show 0
```

### Further Exploration
This is just a quick overview to get you started with OpenNebula. If you liked it, you may want to check the OpenNebula documentation for more information on how to deploy OpenNebula in your infrastructure and a detailed version of the OpenNebula features.

### Troubleshooting
Logs are located in /var/log/one. Be sure to check that in order to troubleshoot. If you need assistance, head out to our forum.


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
