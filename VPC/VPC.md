# 🧠 AWS VPC – Complete Notes on All Components

## 🔹 1. What is a VPC?
**Amazon VPC (Virtual Private Cloud)** is a logically isolated section of AWS where you define your own virtual network environment.

- You can launch AWS resources (like EC2) in a customized network.
- You control IP range, subnets, route tables, gateways, and security settings.

**CIDR Block Example**: `10.0.0.0/16`

---

## 🔹 2. Subnets
A **subnet** is a range of IP addresses in your VPC.

### ▶️ Types:
- **Public Subnet**:
  - Connected to the internet via Internet Gateway.
  - Used for services like Load Balancers, Bastion Hosts, etc.

- **Private Subnet**:
  - No direct internet access.
  - Used for backend services like databases, internal services.

**Note**: Each subnet is bound to one Availability Zone.

---

## 🔹 3. Internet Gateway (IGW)
- Enables communication between instances in your VPC and the internet.
- Must be **attached to a VPC**.
- Route table must have a route to IGW for internet access.

**Use Case**: Public Subnets → Internet Gateway → Internet

---

## 🔹 4. NAT Gateway
Used to provide internet access to instances in **private subnets**, while **preventing inbound traffic**.

### ▶️ Types:
- **NAT Gateway**:
  - Managed by AWS.
  - Highly available and scalable.
- **NAT Instance**:
  - Manually launched EC2 instance.
  - Less reliable, legacy method.

**Use Case**: Private Subnet → NAT Gateway (in Public Subnet) → IGW → Internet

---

## 🔹 5. Route Tables
A **route table** acts as a **virtual router** for subnets in a VPC.

- Controls traffic flow (e.g., send internet traffic to IGW).
- Each subnet must be associated with a route table.
- One main route table is created by default.

**Examples**:
- Public Subnet: `0.0.0.0/0 → IGW`
- Private Subnet: `0.0.0.0/0 → NAT Gateway`

---

## 🔹 6. Elastic IP (EIP)
- A **static public IPv4 address** designed for dynamic cloud computing.
- Can be associated with an EC2 instance or NAT Gateway.
- Useful when a fixed IP is required (e.g., whitelisted IPs).

---

## 🔹 7. VPC Peering
- Allows communication between two VPCs (same or different regions/accounts).
- Uses AWS private IP.
- No transitive peering — direct connection needed for each pair.

---

## 🔹 8. VPC Endpoints
- Enables private connections between your VPC and AWS services **without using the internet**.

### ▶️ Types:
- **Interface Endpoint**: Uses ENI with private IPs.
- **Gateway Endpoint**: Used for S3 and DynamoDB.

---

## 🔹 9. Security Group
- Acts as a **virtual firewall** at the **instance level**.
- Controls inbound and outbound traffic.
- Stateful: return traffic is automatically allowed.

**Example**: Allow inbound SSH from `0.0.0.0/0`, outbound all.

---

## 🔹 10. Network ACL (NACL)
- **Stateless** firewall at the **subnet level**.
- Controls traffic in and out of subnets.
- Rules evaluated in number order, explicitly allow or deny.

**Use Case**: Extra layer of control, e.g., deny a specific IP range.

---

## 🔹 11. VPC Flow Logs
- Captures IP traffic data to and from network interfaces in your VPC.
- Useful for:
  - Troubleshooting network issues
  - Monitoring security
  - Compliance audits

**Log Destinations**: CloudWatch Logs or S3

**Sample Fields**:
- Source IP, Destination IP, Port, Protocol, Action (accept/reject), Bytes transferred, etc.

---

## 🔹 12. Elastic Load Balancer (ELB)
Used to distribute traffic across EC2 instances.

### ▶️ Types:
- **Application Load Balancer (ALB)**: Layer 7 (HTTP/HTTPS)
- **Network Load Balancer (NLB)**: Layer 4 (TCP/UDP)
- **Gateway Load Balancer (GWLB)**: Used with third-party appliances

**Note**: Usually deployed in public subnet, routes traffic to private resources.

---

## 🔹 13. DHCP Option Sets
- Configure **custom domain names**, **NTP servers**, and other settings for instances in a VPC.

---

## 🔹 14. Internet vs Intranet in VPC

| Internet Communication        | Intranet Communication          |
|------------------------------|----------------------------------|
| Via IGW or NAT Gateway       | VPC Peering, Private IPs         |
| Requires public subnet       | Private subnets and VPC routes   |
| Exposes to outside world     | Remains within VPC/AWS network   |

---

## 🔹 Real-World VPC Architecture Example

