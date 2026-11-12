# Homeserver Setup
This repository describes the setup process of my homeservers consisting of one Zorin OS (linux based) machine with a user interface per remote desktop connection and one Ubuntu-Server machine for compute intensive tasks.

# 1) Zorin Machine - Remote Desktop

This machine was set up as a remote desktop server based on Zorin OS designed for visual remote access with a smooth, Windows-like desktop experience.

---

## System Overview
- CPU: 12 Cores, Intel Core i7-8700 @ 3.2 GHz
- No dedicated GPU
- OS: Zorin OS (Linux)
- Goal: Secure and fast remote desktop management via SSH and NoMachine with access ability from external networks.

---

## Key Setup Steps

### 1. SSH & Security Foundation
- Firewall Protection: Configured the local firewall (UFW) to allow incoming SSH connections.
- Authentication: Configured SSH keys of Laptop and Server
- Disabled password authentication and root login, requiring key authentication.
- Brute-Force Protection: Installed Fail2Ban to automatically detect and temporarily ban IPs after repeated failed login attempts.

### 2. Network Configuration
- Port Forwarding: Mapped an external port on the router to the server's internal SSH port.
- Disabled deep sleep states and power management restrictions while enabling Wake-on-LAN.
- Configured the router to automatically wake the server from standby upon incoming external requests.

### 3. Remote Desktop Setup (NoMachine)
- First try with Remotedesktopverbindung on windows gave 1-2 seconds lag
- After switching to NoMachine, the connection is stable and without delay

Now I am able to connect via SSH on my laptop from any network and have the server's desktop mirrored in NoMachine.

# 2) Ubuntu Server Machine - Compute Backend

This machine was set up as a compute dedicated server environment running on Ubuntu Server. It can be accessed by the Zorin System and by my private Laptop via SSH.
The setup steps were similar to the Zorin machine, but  without having to worry about the interface.

---

## System Overview
- CPU: 20 Cores, Intel Core i7-12700 @ 4.9 GHz
- NVIDIA GeForce RTX 3060, 12GB VRAM
- OS: Ubuntu Server (Linux)
- Goal: Compute power with access ability from external networks.

---

# File Sharing
- For file sharing connection between the Windows laptop and the Zorin Server, NoMachine offers an elegant solution to also connect drives between devices
- File sharing between the Windows laptop and the Ubuntu server can easily be implemented using the GUI of WinSCP on the laptop
- The file sharing between the two server machines is enabled by a nfs connection via LAN
