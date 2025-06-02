# VLAN & VTP Based Network Segmentation and Routing Project
 
**Topic**: VLAN Configuration, VTP Management, Trunk Port Settings, Router-on-a-Stick Routing


## 📌Project Objective

The purpose of this project is to enhance network security, manageability, and performance by implementing VLAN segmentation and centralized VLAN management within a network topology. During the configuration process, Cisco devices and Packet Tracer were used to set up trunk links, the VTP protocol, access ports, and router subinterfaces

---

## ⚙️ Configuration Steps

### 1. Enabling Trunk Connections

To allow VLANs to be transmitted between multiple switches in the network, the connections between R1-S1 and S1-S2 have been configured as trunk links:
```bash
Switch(config)# interface FastEthernet0/1
Switch(config-if)# switchport trunk encapsulation dot1q
Switch(config-if)# switchport mode trunk
```
---

### 2. VTP (VLAN Trunking Protocol) Configuration

The VTP protocol has been enabled to centrally manage the VLANs within the network:

**S1 (VTP Server):**

```bash
Switch(config)# vtp domain ktun
Switch(config)# vtp mode server
````
**S2 (VTP Client):**
```bash
Switch(config)# vtp domain ktun
Switch(config)# vtp mode client
````

The configuration can be verified using the **show vtp status** command.

---

### 3. VLAN Definitions and Propagation

The VLANs defined on S1 are automatically propagated to S2 via VTP.

| VLAN ID | VLAN İsmi |
|---------|-----------|
|   21    | personel  |
|   22    | yonetici  |
|   23    | ogrenci   |


```bash
Switch(config)# vlan 21
Switch(config-vlan)# name personel
```
---
### 4. Access Port Configuration

Each computer is connected to an access port configured according to its assigned VLAN.

| PC   | VLAN     | Switch | Port   |
|------|----------|--------|--------|
| PC1  | personel | S1     | Fa0/2  |
| PC3  | personel | S1     | Fa0/3  |
| PC2  | ogrenci  | S2     | Fa0/2  |
| PC6  | ogrenci  | S2     | Fa0/3  |
| PC4  | yonetici | S2     | Fa0/4  |
| PC5  | yonetici | S2     | Fa0/5  |

**Configuration Command:**

```bash
Switch(config)# interface FastEthernet0/x
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan <VLAN ID>
```

---
### 6. Communication and Test Scenarios (Simulation Mode)
Using Packet Tracer's Simulation Mode, the following ping tests were conducted:

PC1 → PC6

PC6 → PC1

During these tests:

Packets passed through R1,

Correct VLAN routing was performed,

Screenshots were taken showing different colors for the forward and return paths.
---
### 📷 Documents and Deliverables

**topology.pka** → Cisco Packet Tracer simulation file

**report.docx** → Configuration steps, test results, and screenshots


---
### ✅ Conclusion
With this configuration:

The network is logically segmented into VLANs,

Centralized management is achieved via the VTP protocol,

Inter-VLAN routing is performed using the Router-on-a-Stick technique.

This project provides a solid practical example of segmentation and routing methods commonly used in small to medium-sized enterprise networks.

**🔒 Note: When implementing on real hardware, all connections should be organized with labeled cables, and configurations must be backed up.**

</details>

---

## 🚀 Uploading to GitHub

Save the README.md file to your project directory.

Use the following Git commands to add and push:

```bash
git add README.md
git commit -m "Add professional README with VLAN/VTP project details"
git push origin main

