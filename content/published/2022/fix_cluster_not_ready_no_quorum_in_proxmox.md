---
title: "Fix 'Cluster not ready - no quorum?' error in Proxmox VE"
tags:
  - linux
  - proxmox
  - virtualization
---

# Purpose
This document will delineate the steps necessary to work around a situation where your Proxmox cluster will not allow you to interact with it due to lack of quorum between the hosts.

# Assumptions
This document assumes that the nodes in the cluster are all online with proper certificates, network connectivity, and that the administrator intents to properly resolve the quorum issue following these steps.

This guide is not intended to be a permanent solution, but rather a work-around.

# Cause
This occurs when the cluster quorum is not configured correctly --or-- when a cluster member is offline. The intended function of the cluster is to not work if the quorum does not receive the adequate number of votes from the cluster to begin. You can manually set the number of expected quorum.

# Workaround
## Step 1 - Override expected number of quorum votes

You can manually set the number of expected quorum votes by running this command:
```bash
pvecm expected #
```

where # is the number of votes you wish to make the quorum use to determine if the cluster is quorate.

>[!warning] Warning
> Take care when manually overriding the cluster quorum, as it can have unintentional results. If a node repeatedly presents an issue, it should be removed form the cluster.

Following use of this command, the cluster should achieve quorum and allow you to interact with it.

---

# Additional Information
- [PVE cluster manager documentation](https://pve.proxmox.com/wiki/Cluster_Manager)
- [PVE forum post on cluster quorum](https://forum.proxmox.com/threads/cluster-and-quorum.7786/)
- [JM Technology post on cluster quorum](https://www.jm.technology/post/proxmox_quorum_april_2019/)