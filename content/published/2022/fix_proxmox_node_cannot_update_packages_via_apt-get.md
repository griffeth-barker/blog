---
title: "Fix Proxmox node cannot update packages via apt-get"
tags:
  - linux
  - proxmox
  - virtualization
---

# **Problem**
A virtualization host/node running Proxmox (whether clustered or not) will fail to update packages via apt-get and produce the below error messages in the task queue:

![](https://audiomgtmoregame.files.wordpress.com/2020/12/image-43.png?w=1024)

# **Environment**
Proxmox Virtualization Environment (confirmed for versions 6.2 and newer) running the free/community editions without and enterprise subscription.

# **Cause**
The cause of this issue results from not having a Proxmox Enterprise subscription/license. These errors are caused by apt-get attempting to procure updates from the subscription enterprise proxmox repository, but because the node or cluster does not have a valid enterprise subscription, the update fails and produces an error.

# **Solution**
Access the shell for the node/virtualization host producing the error and run the following command:

```bash
cp /etc/apt/sources.list.d/pve-enterprise.list /etc/apt/sources.list.d/pve-enterprise.list.backup && echo -e "#$(cat /etc/apt/sources.list.d/pve-enterprise.list)" > /etc/apt/sources.list.d/pve-enterprise.list
```

This command copies the repository sources list, renames the original as a backup so the system does not use it, then comments out the line of the list for the enterprise repository.

Once this command runs successfully, you should be able to either (a) wait for the scheduled updates to try to run again or (b) manually search for and install updates using apt-get update/upgrade. Either way, no errors should be produced.

---

# **Additional Reading**
- [Dannyda.com - How to fix failed to fetch 401 unauthorized task](https://dannyda.com/2020/06/19/how-to-fix-proxmox-pve6-1-26-1-7-update-failedfailed-to-fetch-401-unauthorized-task-error-command-apt-get-update-failed-exit-code-100/)