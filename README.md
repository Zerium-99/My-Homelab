# 🧪 Cyberecurity HomeLab

![Maintained](https://camo.githubusercontent.com/9a2f59491b9d76f507bd6c7ef0074e1bbcfc23b8a7c3e16bc86185ffe79761ee/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4d61696e7461696e65642533462d7965732d677265656e2e7376673f7374796c653d666c61742d737175617265)  [![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)

A hands-on home lab where I experiment, break, and explore systems to learn cybersecurity. Full documentation included.

# ❓ Why a personal Homelab is essential in Cybersecurity

Having a homelab is extremely important in cybersecurity. We can practice, break, build, and test everything we want in an isolated environment, without affecting our real machine. This allows us to gain more experience in the field by putting theory into practice. This allows us to understand better some important cybersecurity concepts: **operating systems**, **networking**, **malware analysis**, **network isolation**, Security Information and Event Management (**SIEM**) and more.

# ✏️ Network Diagram

<img width="621" height="409" alt="network diagram" src="https://github.com/user-attachments/assets/1e422f34-f1a7-4b1f-936d-3d320a8ea826" />

# 💻 Used Resources
Here are the resources I used to make my own cybersecurity homelab:

- Hypervisor: [VirtualBox](https://www.virtualbox.org/)
- Vulnerable machines: [VulnHub](https://vulnhub.com)
- NetworkChuck: https://www.youtube.com/watch?v=mvsiuLzpx2E&t=254s
- Operating System: [Parrot OS](https://parrotsec.org)

# 📦 Virtual Machines
- Attacker Machine:
  - Operating System: [Parrot OS](https://parrotsec.org) 
  - Purpose: Used to perform penetration testing and attacks
  - RAM: 8 GB (8192 MB)
  - CPU Processors: 5
  - Attached to: Internal Network(for isolation)
    
  <img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/8ac16ee5-2f6b-4066-b3cf-a7940a2839ae" />


# 📝 Guide

In this guide, I will walk you through the steps I took to build my own home lab, from scratch.

### 1. VirtualBox Installation

To start, let's install a software that lets us create virtual machines, I chose VirtualBox, because it's simple to use and user-friendly.
I installed it on Windows 11, following the step-by step guide on the official VirtualBox website: https://www.virtualbox.org/

### 2. Choosing the Distro

I chose Parrot OS as my distro for my HomeLab. There are many other ones, such as [Kali Linux](https://kali.org), [Blackarch](https://blackarch.org), [ArchStrike](https://archstrike.org) and even more. Parrot OS is Debian-Based, which makes it stable, well-maintaned and reliable.

### 3. Importing the Parrot OS OVA File

The Parrot OS virtual machine was deployed by importing an existing `.ova` file into VirtualBox. This method ensures a consistent and reproducible environment without requiring a full manual installation.

After importing, the VM was configured with two network adapters:
- NAT adapter for internet access
- Internal Network (intnet) adapter for communication within the lab environment

### 4. Network Isolation

For a safe testing environment, it's fundamental to isolate our VMs, so that all the virtual machines won't be able to communicate to our network.
First, I chose the VM I wanted to isolate, then I clicked on "Settings" and I went to the "Network" Section.

<img width="951" height="595" alt="image" src="https://github.com/user-attachments/assets/8d894246-8f35-4105-88bc-3c14bedf915c" />

The second step I took was to attach the Virtual Machine to the "Internal Network Adapter", then I gave a name to my isolated network: intnet(you can choose every name you want).

### 5. Hosting a DHCP Server

We completed the isolation procedure, but now there's a problem: when we boot our VM, it won't have an assigned IP, to fix this, I hosted a DHCP Server.

On windows, I opened CMD(Command Prompt) and navigated to the path where Oracle Virtual Box is installed C:\Program Files\Oracle\VirtualBox
Then, I hosted my DHCP server by using the following command:

<img width="1475" height="805" alt="image" src="https://github.com/user-attachments/assets/9ae2f27d-8c09-4c2d-bec7-fa69e2dfc6f6" />

After executing the command, I created a DHCP server associated with the internal network (`intnet`). The server was assigned the IP address 10.38.1.1 and configured to automatically distribute IP addresses to connected machines within the range 10.38.1.110–10.38.1.120.

The network was defined with a subnet mask of 255.255.255.0, and the `--enable` flag was used to activate the DHCP service.

### 6. Adding Vulnerable Machines

To start exploiting systems, we need vulnerable virtual machines to attack. I installed multiple vulnerable VMs from [VulnHub](https://vulnhub.com), a great website that offers a wide variety of virtual environments ready to hack. This is very important for our HomeLab, because it gives us the opportunity to train, test, and break systems.

# 🚀 Future Improvements
- Add SIEM
- Add Windows Target
- Add Windows Active Directory lab
