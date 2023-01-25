# hackweek-22-elemental

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