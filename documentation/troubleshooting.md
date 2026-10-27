# Troubleshooting Notes

## 1. VMware Shared Folder Access

### Problem
The shared folder was not initially accessible from the expected directory inside Kali Linux.

### Investigation
I checked the available VMware shared folders using:

```bash
vmware-hgfsclient
```

### Solution
I created a mount point and mounted the shared folders:

```bash
sudo mkdir -p /mnt/hgfs
sudo vmhgfs-fuse .host:/ /mnt/hgfs -o allow_other
```

### Verification
I accessed the `CyberLab-Shared` directory and read the test file.

## 2. Network Configuration

### Observation
The network configuration differed from the reference assignment.

### Commands used

```bash
ip a
ip route
```

### Observed configuration

- IP address: `192.168.10.129/24`
- Default gateway: `192.168.10.2`

### Outcome
I documented the values observed in my VMware environment instead of copying the VirtualBox network settings from the reference project.

## 3. Future Troubleshooting Tasks

- Record DNS configuration.
- Verify gateway and internet connectivity.
- Check whether shared-folder access persists after restarting Kali Linux.
- Document any additional errors and the solutions that resolve them.
