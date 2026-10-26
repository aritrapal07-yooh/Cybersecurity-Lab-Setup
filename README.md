

🔐 Cybersecurity Lab Environment Setup




## Project Overview

This project documents my hands-on experience setting up a Kali Linux virtual machine using VMware Workstation on a Windows 11 host system.

The objective was to create a virtual lab, configure networking, test shared-folder functionality, enable clipboard integration, and save a snapshot of the completed setup.

This project helped me understand the basic configuration and management of a virtual cybersecurity lab.

## Objectives

- Set up Kali Linux in VMware Workstation.
- Check the virtual machine's network configuration.
- Verify network and internet connectivity.
- Configure a shared folder between the host and virtual machine.
- Test file-sharing functionality.
- Enable clipboard integration and drag-and-drop.
- Create a snapshot to preserve the lab's current state.
- Document the process with screenshots.

## Lab Environment

| Component                | Configuration                 |
| ------------------------ | ----------------------------- |
| Host operating system    | Windows 11                    |
| Virtualization software  | VMware Workstation            |
| Guest operating system   | Kali Linux                    |
| Network interface        | eth0                          |
| IP address observed      | 192.168.10.129/24             |
| Default gateway observed | 192.168.10.2                  |
| Shared folder            | CyberLab-Shared               |
| Snapshot                 | Kali-Linux-Lab-Setup-Complete |

*Note: These values describe my observed lab configuration. They differ from the VirtualBox configuration in the reference project.*

## Network Configuration

I checked the network interface and routing information in Kali Linux.

Commands used:

```bash
ip a
ip route
```

The observed network configuration showed:

- Interface: `eth0`
- IP address: `192.168.10.129/24`
- Default gateway: `192.168.10.2`

I also tested connectivity during the setup process.

## Shared Folder Configuration

I configured a VMware shared folder named `CyberLab-Shared`.

To check whether the shared folder was available, I used:

```bash
vmware-hgfsclient
```

I then mounted the shared folders using:

```bash
sudo mkdir -p /mnt/hgfs
sudo vmhgfs-fuse .host:/ /mnt/hgfs -o allow_other
```

The shared folder was accessible at:

```text
/mnt/hgfs/CyberLab-Shared
```

To test file access, I created a test file:

```bash
echo "VMware file sharing works" > /mnt/hgfs/CyberLab-Shared/test.txt
cat /mnt/hgfs/CyberLab-Shared/test.txt
```

The command output confirmed that the test text could be read inside Kali Linux.

## Clipboard and Drag-and-Drop

I enabled the available VMware Guest Isolation options for clipboard and drag-and-drop integration.

I tested clipboard copy-and-paste functionality between the host and guest systems.

## Snapshot

After completing the lab configuration, I created a VMware snapshot named:

`Kali-Linux-Lab-Setup-Complete`

The snapshot provides a saved state that I can return to if I need to recover the lab after future configuration changes.

## Screenshots and Evidence

The `screenshots/` directory contains evidence collected during the setup.

- `01-kali-network.png` — network interface and IP configuration.
- `02-shared-folder.png` — shared-folder mount or access.
- `03-file-sharing-test.png` — test-file creation and reading.
- `04-snapshot.png` — completed snapshot in VMware.

## Challenges and Troubleshooting

One challenge was accessing the VMware shared folder from inside Kali Linux.

I created the mount point and used `vmhgfs-fuse` to mount the shared folders. After that, I was able to access the `CyberLab-Shared` directory and read the test file.

Another important observation was that my lab used VMware Workstation and a `192.168.10.0/24` network, rather than the VirtualBox and `10.0.0.0/24` configuration described in the reference assignment.

## Learning Outcomes


💡 What I Learned



Through this project, I learned how to create and configure a virtual environment for cybersecurity practice.

The most important concepts I learned include:

1. NAT vs NAT Network
A standard NAT configuration and a NAT Network serve different purposes.

A NAT Network allows multiple VMs connected to the same virtual network to communicate with one another while providing network address translation for external connectivity.

This makes it useful for building a multi-machine cybersecurity laboratory.

2. Virtual Machine Networking
I learned how VirtualBox virtual network adapters connect virtual machines to different types of networks and how network configuration affects communication between machines.

3. Static IP Configuration
I learned how to configure and verify IPv4 addressing, subnet masks, gateways, and DNS settings in Kali Linux.

4. VM Snapshots
I learned that a clean snapshot should be created before performing risky or experimental activities.

This provides a known-good recovery point for future cybersecurity exercises.

5. Documentation
I learned that documenting commands, configuration, screenshots, problems, and solutions is an important part of a professional cybersecurity project.


🔐 Security & Ethical Use


This laboratory is intended strictly for education purposes only.

🔗 Tools & Resources


7-Zip: https://7-zip.org/download.html


VirtualBox: https://virtualbox.org/wiki/Downloads




Kali Linux: https://kali.org/get-kali



Through this project, I gained practical experience with:

- Virtual machine configuration.
- Basic Linux network troubleshooting.
- IP addresses, subnets, and default gateways.
- VMware shared folders.
- Host-to-guest integration.
- Virtual machine snapshots.
- Technical documentation and screenshot-based evidence.

## Safety and Intended Use

This lab was created for educational purposes and cybersecurity learning.

Any future security testing will be performed only on systems that I own or have explicit permission to test.

## Author

Aritra Pal


(cyber crime investigator and fraud analyser, ethical hacker)


Linkedln -- https://www.linkedin.com/in/aritrapal07

