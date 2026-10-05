# AWS-VPC-HANDS-ON

# ☁️ AWS VPC — Secure Cloud Networking

<p align="center">
  <img src="https://img.shields.io/badge/AWS-VPC-orange?style=for-the-badge&logo=amazonaws&logoColor=white" />
  <img src="https://img.shields.io/badge/Cloud-Networking-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/DevOps-Hands--On-purple?style=for-the-badge" />
</p>

<p align="center">
  <b>Designing and configuring a secure, scalable virtual network on AWS.</b>
</p>

---

## 🚀 Project Overview

**Amazon VPC (Virtual Private Cloud)** is the foundation of networking in AWS.

In this hands-on project, I designed and configured a custom VPC to understand how AWS resources communicate securely using:

**VPC → Subnets → Route Tables → Internet Gateway → Security Groups → EC2**

This project helped me understand the networking layer behind real-world AWS and DevOps environments.

---

## 🎯 What I Built

```text
┌──────────────────────────────────────────────────────┐
│                     ☁️ AWS CLOUD                     │
│                                                      │
│   ┌──────────────────────────────────────────────┐   │
│   │              🔐 AMAZON VPC                  │   │
│   │                10.0.0.0/16                  │   │
│   │                                              │   │
│   │   ┌──────────────────┐  ┌────────────────┐ │   │
│   │   │ 🌐 Public Subnet │  │ 🔒 Private     │ │   │
│   │   │   10.0.1.0/24    │  │    Subnet      │ │   │
│   │   │                  │  │   10.0.2.0/24  │ │   │
│   │   │   🖥️ EC2         │  │                │ │   │
│   │   └────────┬─────────┘  └────────────────┘ │   │
│   │            │                                │   │
│   │       Route Table                           │   │
│   │            │                                │   │
│   │      🌐 Internet Gateway                   │   │
│   └────────────┼─────────────────────────────────┘   │
│                │                                     │
└────────────────┼─────────────────────────────────────┘
                 │
              🌍 Internet
```

---

## 🧩 AWS Services & Components

| Component               | Role                              |
| ----------------------- | --------------------------------- |
| ☁️ **Amazon VPC**       | Isolated virtual network          |
| 🌐 **Subnets**          | Segment the network               |
| 🚪 **Internet Gateway** | Internet connectivity             |
| 🛣️ **Route Tables**    | Control traffic routing           |
| 🛡️ **Security Groups** | Control instance-level traffic    |
| 🖥️ **EC2**             | Compute resource used for testing |

---

# 🛠️ Implementation

### 01 — Create VPC

Created a custom VPC with:

```text
CIDR → 10.0.0.0/16
```

This provides the private IP address range for the VPC.

---

### 02 — Create Subnets

Configured separate network segments:

```text
🌐 Public Subnet
10.0.1.0/24

🔒 Private Subnet
10.0.2.0/24
```

This separation allows internet-facing and internal resources to be managed independently.

---

### 03 — Configure Internet Gateway

Created and attached an **Internet Gateway** to the VPC.

```text
VPC
 │
 ▼
Internet Gateway
 │
 ▼
🌍 Internet
```

---

### 04 — Configure Route Table

Configured the public route table:

```text
Destination       Target
────────────────────────────
10.0.0.0/16       local
0.0.0.0/0         Internet Gateway
```

The `0.0.0.0/0` route allows internet-bound traffic through the Internet Gateway.

---

### 05 — Configure Security Group

Configured inbound access according to the application requirement.

| Protocol |  Port | Purpose               |
| -------- | ----: | --------------------- |
| SSH      |  `22` | Remote administration |
| HTTP     |  `80` | Web traffic           |
| HTTPS    | `443` | Secure web traffic    |

🔐 **Best Practice:** SSH should be restricted to trusted IP addresses rather than being open to the entire internet.

---

### 06 — Launch EC2

Launched an EC2 instance inside the VPC and used it to test:

```text
✓ Internet connectivity
✓ SSH connectivity
✓ Security Group rules
✓ Public IP access
✓ Network configuration
```

---

# 🔄 Network Traffic Flow

```text
              🌍 INTERNET
                   │
                   ▼
          ┌─────────────────┐
          │ Internet Gateway│
          └────────┬────────┘
                   │
                   ▼
             🛣️ Route Table
                   │
                   ▼
          ┌─────────────────┐
          │  Public Subnet  │
          └────────┬────────┘
                   │
                   ▼
            🛡️ Security Group
                   │
                   ▼
             🖥️ EC2 Instance
```

---

# 🧠 Key Concepts Learned

### ☁️ VPC

Provides an isolated networking environment in AWS.

### 🌐 Subnet

Divides a VPC into smaller network segments.

### 🚪 Internet Gateway

Enables communication between a VPC and the internet when routing and addressing are configured appropriately.

### 🛣️ Route Table

Determines where network traffic is directed.

### 🛡️ Security Group

Acts as a virtual firewall controlling traffic to and from supported AWS resources.

### 📦 CIDR

Defines the IP address range available within the network.

---

# 🌍 Real-World Architecture

VPC networking forms the foundation of many production architectures.

```text
                       🌍 USERS
                          │
                          ▼
                 ┌─────────────────┐
                 │ Application      │
                 │ Load Balancer    │
                 └────────┬────────┘
                          │
                          ▼
              ┌──────────────────────┐
              │ Application Servers  │
              │      EC2 / ECS       │
              └──────────┬───────────┘
                         │
                         ▼
              ┌──────────────────────┐
              │      Database        │
              │   RDS / Aurora       │
              └──────────────────────┘
```

This type of architecture can be extended into a **highly available 3-tier application** using multiple Availability Zones and private networking.

---

# 🔐 Security Focus

This project also helped me understand basic cloud network security:

```text
🔒 Network Isolation
        ↓
🛡️ Security Groups
        ↓
🚫 Restrict Unnecessary Ports
        ↓
🔑 Secure SSH Access
        ↓
🏗️ Private Subnets for Internal Resources
```

---

# 📚 Key Takeaways

> **VPC is the networking foundation of AWS.**

Through this project, I gained practical understanding of:

* ✅ AWS VPC architecture
* ✅ CIDR addressing
* ✅ Public vs Private Subnets
* ✅ Route Tables
* ✅ Internet Gateway
* ✅ Security Groups
* ✅ EC2 networking
* ✅ Basic cloud network security
* ✅ Production-oriented network design

---

# 🚀 Future Enhancements

I plan to extend this architecture with:

```text
☑ NAT Gateway
☑ Multiple Availability Zones
☑ Application Load Balancer
☑ Auto Scaling
☑ Private EC2 Instances
☑ Amazon RDS
☑ VPC Flow Logs
☑ Bastion Host
☑ VPC Peering
☑ Terraform Infrastructure as Code
```

---

# 📸 Project Screenshots

Add your AWS Console screenshots here:

```text
📁 screenshots/

├── 01-vpc.png
├── 02-subnets.png
├── 03-route-table.png
├── 04-internet-gateway.png
├── 05-security-group.png
└── 06-ec2.png
```

Example:

```html
<p align="center">
  <img src="screenshots/01-vpc.png" width="850">
</p>
```

---

# 🛠️ Tech Stack

<p align="center">

`AWS` • `VPC` • `EC2` • `Linux` • `Networking` • `Cloud` • `DevOps`

</p>

---

# 👨‍💻 About Me

**Vishwajit Hulawale**

🎯 Aspiring **AWS DevOps / Cloud Engineer**

Currently building practical skills in:

**AWS • DevOps • Linux • Cloud Infrastructure • Networking**

---

## ⭐ Project

If you found this project useful, consider giving it a ⭐

**Built while learning AWS DevOps through hands-on practice.**

---
