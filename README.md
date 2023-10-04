# Raspberry Pi Cluster Setup Guide

![FKSPf9FXMAcqNJ7](https://github.com/Ravenneo/MiniCluster/assets/41577767/c5037c2e-8e3f-4bd1-a602-bbb986ba4dfd)


This guide will help you set up a simple Raspberry Pi cluster with two Raspberry Pi Zero W devices using static IP addresses for easy management and communication between them. This cluster setup is ideal for various projects and experiments.

## Prerequisites

Before you begin, make sure you have the following:

- Two Raspberry Pi Zero W devices
- A computer with an SSH client (for remote access)
- A microSD card with Raspberry Pi OS (Raspbian) installed
- Access to your local network

## Steps

**Step 1: Connect to Your Raspberry Pi Devices**

Use SSH to connect to your Raspberry Pi Zero W devices:

ssh pi@raspberrypi.local


Replace `raspberrypi.local` with the IP address of your Raspberry Pi if you've already set it up with a static IP.

**Step 2: Open the Network Configuration File**

On each Raspberry Pi, open the network configuration file for editing:

sudo nano /etc/dhcpcd.conf


**Step 3: Add Static IP Configurations**

Add static IP configurations for each Raspberry Pi in the `dhcpcd.conf` file. Replace the IP addresses with the ones you want to assign. For example:

For Raspberry Pi A:

interface wlan0
static ip_address=192.168.0.41/24
static routers=192.168.0.1
static domain_name_servers=192.168.0.1

For Raspberry Pi B:

interface wlan0
static ip_address=192.168.0.42/24
static routers=192.168.0.1
static domain_name_servers=192.168.0.1


**Step 4: Save and Exit**

Save your changes and exit the text editor.


**Step 5: Reboot Raspberry Pis**

Reboot both Raspberry Pis to apply the new static IP configurations:

sudo reboot


**Step 6: Verify IP Addresses**

After the Raspberry Pis have rebooted, verify that the static IP addresses are assigned correctly:

ssh pi@192.168.0.41
ssh pi@192.168.0.42


**Step 7: Set Up Cluster Software**

Choose and install cluster management software, such as Docker or Kubernetes, to manage applications across your Raspberry Pis. Follow the respective setup guides for your chosen software.


**Step 8: Test Communication**

Test communication between the Raspberry Pis by SSHing into one of them and pinging the other:

From Raspberry Pi A:

ping 192.168.0.42

From Raspberry Pi B:

ping 192.168.0.41

If the pings are successful, it means the Raspberry Pis can communicate with each other over the network.
Conclusion

You've successfully set up a Raspberry Pi cluster with static IP addresses, making it easier to manage and communicate between the devices. You can now use this cluster for various projects and experiments.
