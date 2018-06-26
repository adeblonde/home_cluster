# Home Cluster

This project is mainly a library of documentations and tutorials aimed at creating and configuring a Data/Machine Learning/Automation system at your home, using your own devices.

## Setting up your home network

### Personal router

First of all, you need to invest in a personal router, that will create your local network, instead of your Internet Provider's box, for security reasons : if you keep your provider's box as your home network's root, all of the network traffic between your devices can be scanned by your provider.

You can easily find good models of routers at TP-Link, Linksys or NetGear. Choose a model with a good number of ethernet Gigabyte ports (> 4, depending on how many devices you plan to gather and connect)

Once you have your router, connect it AFTER your provider's box with an ethernet gigabyte cable. You will probably need to set your box in 'Bridge' mode. If you are located in France, Free and FDN are currently the only providers wuth a 'Bridge' mode on their box.

### Permanent local IP addresses

A good practice in your home network would be to set permanent IP addresses for has much devices as possible.
For TP-Link routers, you can usually connect to your router's web administration console by calling `192.168.0.1` in your browser address bar.
There, permanent IP addresses will probably be set in 'DHCP options'

It would be necessary also to note the emac addresses of your devices, especially for Wake-on-Lan options (see below)

You can get the local IP addresses of all the devices of your local network with the following command :

```bash
arp-scan -l
```

You can get the emac address of your current device with the following command :

```bash
ip addr
```

or, for older versions of linux :

```bash
ifconfig
```

### SSH activation and securization

In order to easily connect to all of the devices of your home network, you will need to setup OpenSSH server on all of them, then to create secure SSH connections between them, by disabling password connections

https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04

### Firewall activation

To avoid bad surprises on your home installation, a good firewall is necessary

### Wake on Lan setup

In our cluster configuration, we plan to reuse old laptops and old PC, and convert them into test servers. The hardware setup of a laptop is slightly different than the one of a server (disk type, power supply, etc). Some tweaks allow to use a laptop or a normal PC as a server while sparing its disks, but the best option is to allow them to shutdown when not needed. For this, we need the possibility to power on them again remotely, through Wake-on-Lan (WoL).

https://doc.ubuntu-fr.org/wakeonlan

### NFS setup

NFS stands for Network File Sharing. It is a efficient file sharing protocol used by Unix-like computers to provide efficient mounting of folders on a network. To ease communications on your home cluster, we will mount all of the home and/or data folders of all devices on your master device.

https://wiki.debian.org/NFSServerSetup

### Samba Share setup

Samba is another file sharing protocol, coming from the Microsoft ecosystem, for which Unix versions are easily available. We will use them to allow folders sharing with Windows computers on your network.

### Local VPN setup

Your whole home cluster is designed to be unreachable from the outside, except from manually chosen entry points (SSH on the NAS server, for example). In order to use the whole potential of your cluster when you are not at home, we will setup a VPN server, so that you can access all the devices of your home network securely.

## Installing a NAS/HTPC server

A NAS server is a particular machine chosen to be up all of the time. Its hardware must be chosen in that way : server HDD drive (slightly more costly than common PC HDD), low-consumption motherboard and CPU. You can install on this machine various services of your own cloud :

- Kodi (Media Server)
- Nextcloud (File Sharing, Address Book, Calendar synchronization, etc)
- Websites

## Installing Nextcloud on your NAS

Nextcloud is a 'personal cloud' open source solution, targeted at providing File Sharing, Address Book, Calendar synchronization, and a lot of other stuff
https://nextcloud.com/support/

## Installing Syncthing on your NAS

Syncthing is a file synchronization tool, that can replace the File Sharing feature of Owncloud, with some drawback, while being lighter and easier to use. Their use cases are slightly different.

## Installing a blog server on your NAS (Wordpress)

We will install a Wordpress blog on your NAS, powered by an Nginx http server.

## Installing a Gitlab instance on your server

Gitlab is an open source efficient file versioning and forge software.

## Intalling a photo service on your NAS (Piwigo)

You can install a photo sharing service on your NAS server. There are many open source solutions for that feature, we chose Piwigo :
https://fr.piwigo.org/

## Installing a vocal assistant

We choose Mycroft as an open source vocal Intelligent Personal Assistant (IPA) : 
https://mycroft.ai/

## Installing an AI server

Mycroft do not provide currently a purely home and offline solution for Speech To Text (STT). We will setup a dedicated server with an old GPU to serve as a STT, and potentially as an image recognition service.

As an open source STT server, we chose Mozilla's DeepSpeech :
https://github.com/mozilla/DeepSpeech

## Connecting drones to your home network

Not implemented yet

## Installing an Hadoop cluster on your home network

Not imlemented yet