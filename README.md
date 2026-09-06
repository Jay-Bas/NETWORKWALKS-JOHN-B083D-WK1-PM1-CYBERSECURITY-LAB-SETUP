# VirtualBox Cybersecurity Lab

## Project Overview

A hands-on cybersecurity laboratory built using Oracle VirtualBox, Kali Linux, and Windows 11.

The project focused on creating an isolated virtual environment where security tools, networking concepts, and future cybersecurity exercises can be practiced safely.

The lab was configured using a custom VirtualBox NAT Network with the `10.0.0.0/24` address range.

## Lab Environment

- Host OS: Windows 11
- Hypervisor: Oracle VirtualBox
- Kali Linux: Virtual Machine
- Windows 11: Virtual Machine
- Network Type: Custom NAT Network
- Network Name: `NatNetwork`
- Network Address: `10.0.0.0/24`
- DHCP: Enabled

## Lab Network

| Device | IP Address |
|---|---|
| Kali Linux | `10.0.0.3/24` |
| Windows 11 | `10.0.0.4/24` |

Both virtual machines were connected to the same custom NAT Network.

---

# Phase 1 – Kali Linux Setup

## 1. Install 7-Zip

Installed 7-Zip to extract the Kali Linux VirtualBox image.

## 2. Create the NAT Network

Created a custom VirtualBox NAT Network:

- Network Name: `NatNetwork`
- IPv4 Network: `10.0.0.0/24`
- DHCP: Enabled

## 3. Import Kali Linux

Downloaded the official Kali Linux VirtualBox image, extracted the archive, and imported the `.vbox` file into Oracle VirtualBox.

## 4. Configure Kali Network Adapter

Configured Kali Linux Adapter 1 to use:

`NAT Network → NatNetwork`

## 5. Verify Kali IP Address

Used the Linux `ip a` command to verify the assigned IP address.

Kali Linux received:

`10.0.0.3/24`

## 6. Create Recovery Snapshot

Created a clean recovery snapshot:

`Clean Kali - Network Ready - Phase 1`

This provides a known-good state for future cybersecurity laboratory exercises.

---

# Phase 2 – Windows 11 Setup

## 1. Windows 11 ISO

Downloaded the official Windows 11 x64 ISO from Microsoft.

## 2. Create Windows 11 Virtual Machine

Created a Windows 11 virtual machine with:

- 4 GB RAM
- 2 CPUs
- UEFI
- 80 GB virtual disk
- `NatNetwork` network connection

## 3. Install Windows 11

Completed the Windows 11 installation process and successfully reached the Windows desktop.

## 4. Configure Network

Connected the Windows 11 virtual machine to the same:

`NatNetwork`

## 5. Verify Windows IP Address

Used:

`ipconfig`

Windows 11 received:

`10.0.0.4/24`

---

# Connectivity Verification

Both virtual machines were started simultaneously to verify that the laboratory network was functioning correctly.

## Ping Test

From Windows 11:

`10.0.0.4`

To Kali Linux:

`10.0.0.3`

### Result

**PING SUCCESSFUL**

- Packet loss: `0%`
- Connectivity: Successful

This confirmed that the two virtual machines could communicate across the custom VirtualBox NAT Network.

---

# Virtual Machine Snapshots

Snapshots were created to preserve clean recovery points for future laboratory work.

| Virtual Machine | Snapshot | Purpose |
|---|---|---|
| Kali Linux | `Clean Kali - Network Ready - Phase 1` | Clean state after network configuration |
| Windows 11 | `Clean Windows 11 - After Install - Phase 2` | Clean state after installation and network configuration |

Snapshots allow the laboratory environment to be restored to a known working state before performing future security exercises.

---

# Network Topology

```text
                    Internet
                       |
                       |
              Windows 11 Host
              Physical Machine
                       |
                       |
                Oracle VirtualBox
                       |
                       |
              NatNetwork
              10.0.0.0/24
                /          \
               /            \
              /              \
       Kali Linux          Windows 11
       10.0.0.3            10.0.0.4
