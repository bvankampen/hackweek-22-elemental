# hackweek-22-elemental

*This is draft documentation*

## Project Description

We have a lot of solutions for the Edge like: Rancher, k3s, Elemental, SLE Micro but we don't have a complete end to end example solution the deliver these. For example if a Edge device at a customer location  fails somebody without any knowledge should be able the replace the device. The installation and provisioning should be automatic, this should also be for new devices.

## Goals for this Hackweek

- Automated generation of the Elemental image
- Automated creation of the cluster and configuration in Rancher
-  A method to deliver this image to the edge device (via network)
- Installation of the operation system and K3s on the edge device
- Joining the Edge Device to the Cluster
- Installing the software on K3s on the Edge device (fleet)
- Logging and Monitoring

## Resources

- [https://elemental.docs.rancher.com](https://elemental.docs.rancher.com/)
- [https://github.com/bvankampen/hackweek-22-elemental](https://github.com/bvankampen/hackweek-22-elemental)

## Cluster Prerequisites

This is a example to install elemental over the network, for the elemental nodes kvm virtualization is used.

All ansible playbooks are in folder `ansible`

### Rancher Extensions

Enables Rancher extensions and install the elemental extension.

### Boot server

- Install dnsmasq
- Install nginx
    Point rootdir to /srv/tftpboot

### Install Elemental Operator

```shell
ansible-playbook install_elemental_operator.yml
```

If a PSP is need change `install_psp: no` in `install_elemental_operator.yml`

## Create and run example environment

###  Install common boot files and dns config

Check and change template files in `ansible/roles/copy_common_boot_files/templates/`

```shell
ansible-playbook common_bootfiles.yml
```

### Create and upload ISO and create cluster

Check and configure:

```shell
ansible/group_vars/all.yml
ansible/cluster_1.yml
```

Run the playbook

```shell
ansible-playbook create_cluster.yml -e @cluster_1.yml
```

To create to KVM vm's run the playbook

```shell
ansible-playbook create_vms.yml -e @cluster_1.yml
```
