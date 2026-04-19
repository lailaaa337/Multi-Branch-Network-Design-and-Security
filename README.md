
#  Network Design & Security (Multi-Branch Enterprise Network)

##  Overview
This project focuses on designing and securing a **multi-branch enterprise network** connecting multiple cities including:

- Cairo  
- Alexandria  
- Aswan  
- Port Said  
- Luxor  
- Dubai  

The system integrates **network design, routing, VLAN segmentation, and security mechanisms** to ensure efficient communication and protection of critical resources.

> The project simulates a real-world corporate network with multiple departments and security layers :contentReference[oaicite:0]{index=0}.

---

##  Features

-  Multi-branch network architecture  
-  VLAN segmentation for departments  
-  Static and dynamic routing (OSPF)  
-  Access Control Lists (ACLs) for security  
-  Firewall-like behavior using ACLs  
-  Secure wireless configuration (WPA2)  
-  Real network simulation using Cisco Packet Tracer  

---

##  Network Architecture

The network consists of:

-  **6 Routers** (one per branch)  
-  **Switches** for each department  
-  **Access Points** for wireless connectivity  
-  PCs and Laptops across departments  
-  Central **Web/DNS Server**

> The topology diagrams (pages 10–11) illustrate interconnections between branches and departments :contentReference[oaicite:1]{index=1}.

---

##  Subnetting Design

Each branch is assigned a dedicated network:

| Branch       | Network      | Users |
|-------------|-------------|------|
| Alexandria  | 11.0.0.0     | 256  |
| Cairo       | 13.0.0.0     | 1000 |
| Aswan       | 15.0.0.0     | 60   |
| Port Said   | 17.0.0.0     | 120  |
| Luxor       | 19.0.0.0     | 50   |
| Dubai       | 21.0.0.0     | 500  |

> Subnetting is designed based on user requirements per branch :contentReference[oaicite:2]{index=2}.

---

##  VLAN Configuration

Departments are separated using VLANs:

- IT → VLAN 5  
- Security → VLAN 10  
- Core Operations → VLAN 15  
- Finance → VLAN 20  
- Marketing → VLAN 25  
- HR → VLAN 30  
- Customer Service → VLAN 35  

 VLANs ensure:
- Network isolation  
- Improved security  
- Efficient traffic management  

---

##  Routing Configuration

###  Static Routing
Used to manually define paths between branches.

Example:

```bash
ip route 13.0.0.0 255.255.255.0 12.0.0.1
````

---

###  Dynamic Routing (OSPF)

OSPF is implemented between branches (e.g., Aswan & Luxor):

```bash
router ospf 1
network 15.0.0.0 0.255.255.255 area 0
network 19.0.0.0 0.255.255.255 area 0
```

 Benefits:

* Automatic route updates
* Efficient path selection

> OSPF configuration is detailed on pages 6–7 .

---

##  Security Implementation

###  Access Control Lists (ACLs)

ACLs are used to restrict unauthorized access:

* Block Dubai R&D → Finance Network
* Block Dubai R&D → DNS/Web Server
* Allow authorized communication

Example:

```bash
access-list 100 deny ip 21.0.0.0 0.255.255.255 13.0.20.0 0.0.0.255
```

> ACL configuration acts as a basic firewall on the Cairo router .

---

###  Firewall Behavior

* Controls traffic between networks
* Protects sensitive resources
* Allows selective communication

---

###  Wireless Security

* SSID: **Alexandria**
* Encryption: **WPA2-PSK**
* Secure authentication implemented

> Wireless configuration ensures secure access for clients .

---

##  Testing & Results

| Source            | Destination     | Result    |
| ----------------- | --------------- | --------- |
| Dubai (R&D)       | DNS/Web Server  |  Blocked  |
| Dubai (R&D)       | Finance Network |  Blocked  |
| Cairo (Finance)   | DNS/Web Server  |  Allowed  |
| Alexandria (WiFi) | DNS/Web Server  |  Allowed  |

> Testing confirms correct implementation of security policies .

---

##  Technologies Used

* **Cisco Packet Tracer**
* Networking Protocols (IP, OSPF)
* VLANs & Subnetting
* ACLs & Network Security Concepts

---

##  Project Structure

```
project/
│── networksPrj.pkt        # Packet Tracer simulation
│── networksdocumentation.pdf
│── README.md
```

---

##  Project Documentation

 Full report available here:
[View Report](networksdocumentation.pdf)

---

##  What I Learned

* Designing enterprise-scale networks
* Subnetting and IP planning
* VLAN configuration and segmentation
* Static vs dynamic routing (OSPF)
* Implementing ACLs for security
* Simulating real networks using Packet Tracer

---

##  Limitations

* Simulation-based (no real hardware)
* Limited scalability testing
* Basic firewall implementation

---

##  Future Improvements

* Add real firewall devices (ASA)
* Implement advanced security (IDS/IPS)
* Use dynamic IP allocation (DHCP)
* Expand to cloud networking
* Improve monitoring and logging

---

##  Team Members

* Laila Tarek
* Hana Tariq

---

##  Disclaimer

This project is for **educational purposes only**.

```

