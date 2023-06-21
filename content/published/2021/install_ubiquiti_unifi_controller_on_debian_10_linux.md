---
title: "Install Ubiquiti UniFi controller on Debian 10 Linux"
tags:
  - linux
  - unifi
  - ubiquiti
---

# Prerequisites

If you’re installing on Linux, be sure you have the following ahead of time:

- A current Debian or Ubuntu OS with root access – The steps will use [Debian 10](https://www.blogger.com/blog/post/edit/8562458718891840214/6386954631595199676#)
- An account for [unifi.ui.com](https://www.blogger.com/blog/post/edit/8562458718891840214/6386954631595199676#)

And that’s it. Everything else will be handled during the install process.

# Installing the Controller

To get the controller installed on Linux you have many options. Ubiquiti has some instructions on how to install the controller on their website but it only covers the install for a couple of specific versions of Linux. To use Debian, use the script that has been posted on the [Unifi forums](https://www.blogger.com/blog/post/edit/8562458718891840214/6386954631595199676#) by member AmazedMender16.

To start the install, first ssh into the Debian server or access the server from the console. Log in either as root or as another user that has root access and then run su.

Make sure your repos are up to date, then install the `ca-certificates` and `wget` packages.
```bash
apt-get update && apt-get install ca-certificates wget -y
```

Download and run the Unifi Controller installer script. This script will handle the install of the dependencies and controller software for many different distros of Linux including the Debian 10 server we are using.
```bash
wget https://get.glennr.nl/unifi/install/install_latest/unifi-latest.sh1 bash unifi-latest.sh
```

You will be prompted for a few things while the script runs. First, it will ask if you want to keep the script downloaded after the install. In most cases this is not required, so you should enter `n` and then press enter.

# Ensuring the Unifi controller software is up to date

You may receive a prompt to update packages during the install. Enter `y` and then press enter.

# Confirming it’s OK to update packages

Finally, you will be prompted to add the apt repo for Unifi to update the controller from apt. Enter `y` and press enter as this will make upgrades serviceable through apt.

Once the install completes, the script will output the version of the controller installed and the URL to use to start configuring the controller.

# Configuring the Controller

Once you have the controller software installed on whatever server you are using the setting will be the same.

Go to the web address `https://<ServerIP>:8443/` and you will be presented with the controller's web portal.