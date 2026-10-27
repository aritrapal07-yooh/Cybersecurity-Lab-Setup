# Cybersecurity Lab Setup: Kali Linux on VMware

 
**Field:** Computer Science Engineering  
**Project Type:** Hands-on Cybersecurity Lab Setup

## 1. Project Overview

This project documents my experience setting up a Kali Linux virtual machine using VMware Workstation on a Windows 11 computer.

The main objective was to configure a virtual lab, examine network connectivity, test VMware shared-folder functionality, enable host-to-guest integration, and create a snapshot of the configured virtual machine.

This project helped me develop practical skills in Linux, virtualisation, basic networking, troubleshooting, and technical documentation.

## 2. Project Objectives

- Set up Kali Linux in VMware Workstation.
- Inspect network interfaces and routing information.
- Test network and internet connectivity.
- Configure a VMware shared folder.
- Test file access between the host and guest environment.
- Enable clipboard and drag-and-drop integration.
- Create a snapshot of the virtual machine.
- Document the configuration and verification process.

## 3. Lab Environment

| Component | Configuration |
|---|---|
| Host operating system | Windows 11 |
| Virtualisation software | VMware Workstation |
| Guest operating system | Kali Linux |
| Network interface | eth0 |
| Observed IP address | 192.168.10.129/24 |
| Observed default gateway | 192.168.10.2 |
| VMware shared folder | CyberLab-Shared |
| Snapshot name | Kali-Linux-Lab-Setup-Complete |

**Note:** These network values describe my observed configuration. They may change if the virtual machine receives a different address. This setup uses VMware Workstation rather than the VirtualBox configuration in the reference project.

## 4. Network Configuration

I inspected the network interface and routing table in Kali Linux using:

```bash
ip a
ip route
```

The configuration observed during setup was:

- Network interface: `eth0`
- IP address: `192.168.10.129/24`
- Default gateway: `192.168.10.2`

These commands helped me understand the assigned IP address, subnet, and default route.

## 5. Network Verification

I used network diagnostic commands to check connectivity.

```bash
ip a
ip route
ping -c 4 192.168.10.2
ping -c 4 8.8.8.8
nslookup example.com
```

The first two commands display network configuration. The remaining commands test gateway reachability, connectivity to a public IP address, and DNS resolution.

**Test results:** I will record the actual results of these checks rather than assuming every test succeeds.

## 6. VMware Shared Folder Configuration

I configured a VMware shared folder named `CyberLab-Shared`.

To check the shared folders available to Kali Linux, I used:

```bash
vmware-hgfsclient
```

I created a mount point and mounted the shared folders using:

```bash
sudo mkdir -p /mnt/hgfs
sudo vmhgfs-fuse .host:/ /mnt/hgfs -o allow_other
```

The shared folder was accessible at:

```text
/mnt/hgfs/CyberLab-Shared
```

### File-Sharing Test

I created a test file in the shared folder:

```bash
echo "VMware file sharing works" > /mnt/hgfs/CyberLab-Shared/test.txt
```

I then read the file:

```bash
cat /mnt/hgfs/CyberLab-Shared/test.txt
```

The output confirmed that the test text could be read from inside Kali Linux.

## 7. Clipboard and Drag-and-Drop

I enabled the available VMware Guest Isolation options for clipboard and drag-and-drop integration.

I tested clipboard copy-and-paste functionality between the host and guest systems.

## 8. Snapshot Management

After configuring the lab, I created a VMware snapshot named:

`Kali-Linux-Lab-Setup-Complete`

The snapshot provides a saved state that can be used to return the virtual machine to this configuration if future changes cause problems.

## 9. Verification Checklist

| Check | Verification method | Status |
|---|---|---|
| Network interface | `ip a` | Configuration observed |
| Default route | `ip route` | Configuration observed |
| Gateway connectivity | Ping the observed gateway | Record actual result |
| Public IP connectivity | Ping `8.8.8.8` | Record actual result |
| DNS resolution | `nslookup example.com` | Record actual result |
| Shared-folder detection | `vmware-hgfsclient` | Previously observed |
| Test-file access | Read `test.txt` | Previously verified inside Kali |
| Clipboard integration | Host-to-guest copy and paste | Tested |
| Snapshot | Inspect VMware snapshot manager | Created |

## 10. Troubleshooting

### Issue: Shared Folder Not Immediately Accessible

**Problem:** The shared folder was not initially accessible from the expected directory in Kali Linux.

**Solution:** I created the `/mnt/hgfs` mount point and used `vmhgfs-fuse` to mount the VMware shared folders.

**Verification:** I accessed the `CyberLab-Shared` directory and read the test file.

### Network Configuration Difference

My lab uses VMware Workstation and an observed IP address of `192.168.10.129/24`. This differs from the `10.0.0.0/24` network described in the reference assignment.

I documented the configuration actually observed in my environment instead of presenting the reference project's network settings as my own.

## 11. Learning Outcomes

Through this project, I gained practical experience with:

- Kali Linux virtual machine setup.
- IP addressing and subnet notation.
- Linux network interfaces and routing tables.
- Basic connectivity troubleshooting.
- VMware shared folders.
- File access between host and guest environments.
- Clipboard and drag-and-drop integration.
- Virtual machine snapshots.
- Technical documentation using Markdown.

## 12. Future Improvements

Possible future improvements include:

- Documenting VMware NAT, bridged, and host-only networking.
- Recording detailed results for every connectivity test.
- Testing shared-folder availability after restarting the virtual machine.
- Practising packet analysis using Wireshark in an authorised lab.
- Learning basic Nmap discovery and enumeration techniques on systems I own or have permission to test.
- Building a separate practice environment for authorised security testing.

These are planned improvements, not completed features.

## 13. Safety and Intended Use

This project was created for educational purposes and cybersecurity learning.

Any future security testing will be restricted to systems I own or have explicit permission to test.

## 14. References

- [Kali Linux Documentation](https://www.kali.org/docs/)
- [VMware and Broadcom Technical Documentation](https://techdocs.broadcom.com/)
- [GitHub README Documentation](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes)

## Author

Aritra Pal


Computer Science Engineering Student  
Interested in Cybersecurity and Ethical Hacking
