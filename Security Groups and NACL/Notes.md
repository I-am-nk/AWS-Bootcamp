
# AWS Security using Security Groups and NACL

AWS (Amazon Web Services) provides multiple layers of security to protect resources and data within its cloud infrastructure. Two important components for network security in AWS are **Security Groups** and **Network Access Control Lists (NACLs)**. Let's explore how each of them works:

## 🔐 Security Groups

- Security Groups act as virtual firewalls for Amazon EC2 instances (virtual servers) at the instance level.
- They control inbound and outbound traffic by allowing or denying specific protocols, ports, and IP addresses.
- Each EC2 instance can be associated with one or more security groups, and each security group consists of inbound and outbound rules.
- **Inbound rules** determine the traffic that is allowed to reach the EC2 instance.
- **Outbound rules** control the traffic leaving the instance.
- Security Groups can be configured using IP addresses, CIDR blocks, security group IDs, or DNS names to specify the source or destination of the traffic.
- They operate at the **instance level** and evaluate the rules before allowing traffic to reach the instance.
- Security Groups are **stateful**, meaning that if an inbound rule allows traffic, the corresponding outbound traffic is automatically allowed, and vice versa.
- Changes made to security group rules **take effect immediately**.

## 🌐 Network Access Control Lists (NACLs)

- NACLs are an additional layer of security that operates at the **subnet level**.
- They act as stateless traffic filters for inbound and outbound traffic at the subnet boundary.
- Unlike Security Groups, NACLs are associated with subnets, and **each subnet can have only one NACL**.
- However, **multiple subnets can share the same NACL**.
- NACLs consist of a numbered list of rules (evaluated from lowest to highest).
- Each rule in the NACL includes:
  - Rule number
  - Protocol
  - Rule action (allow or deny)
  - Source or destination IP address range
  - Port range
  - ICMP (Internet Control Message Protocol) type
- NACL rules can be configured to allow or deny specific types of traffic based on the defined criteria.
- They are **stateless**, which means if an inbound rule allows traffic, the corresponding outbound traffic must also be explicitly allowed.
- Changes made to NACL rules **may take time** to propagate to all the resources using the associated subnet.

---

![image](https://github.com/user-attachments/assets/75a5d075-776f-4ab8-9ca3-3b53308fee11)

