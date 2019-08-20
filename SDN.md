---
title: SDN
tags: Intern, SDN
description: SDN
---
## OpenFlow 
- Open Networking Foundation: The key of SDN is the separation of control plane and data plane.
-  Network devices(switches & routers) have control plane for brain-like functions and data plane for forwarding packets.'
-  OpenFlow: an open standard for a communications protocol that enables the control plane to break off and interact with the forwarding plane of multiple devices from some central point, decoupling roles for higher functionality and programmability
![](https://i.imgur.com/U9F7geI.png)

## Need for Network Abstraction
-  Abstraction capability could be done with a controller layer
-  The application developer can use an API to communicate to the controller
![](https://i.imgur.com/vvjKMLg.png)
- OpenFlow updates the flow tables of network devices instead of configurations on network devices.

# Open Switch 
## Open vSwitch (OVS)
- multilayer virtual switch implemented in software
- use virtual network bridges and flow rules to forward packets between hosts

## Open vSwitch Flow Forwarding
- Kernel mode, known as “fast path” processing is where it does the switching.
- User mode, is known as “slow path”.