# 🔬 Labs: Network Advanced

---

## 🔬 Lab 1: VPC Design

Design VPC với:

- 2 Availability Zones
- Public và Private subnets
- NAT Gateway
- Internet Gateway

---

## 🔬 Lab 2: Security Groups

```bash
# AWS CLI - Create Security Group
aws ec2 create-security-group \
  --group-name web-sg \
  --description "Web server SG" \
  --vpc-id vpc-xxx

# Add rules
aws ec2 authorize-security-group-ingress \
  --group-id sg-xxx \
  --protocol tcp \
  --port 80 \
  --cidr 0.0.0.0/0

aws ec2 authorize-security-group-ingress \
  --group-id sg-xxx \
  --protocol tcp \
  --port 443 \
  --cidr 0.0.0.0/0
```

---

## 🔬 Lab 3: Application Load Balancer

```bash
# Create ALB
aws elbv2 create-load-balancer \
  --name my-alb \
  --subnets subnet-xxx subnet-yyy \
  --security-groups sg-xxx

# Create Target Group
aws elbv2 create-target-group \
  --name my-targets \
  --protocol HTTP \
  --port 80 \
  --vpc-id vpc-xxx \
  --health-check-path /health
```

---

## 🔬 Lab 4: VPC Peering

Connect 2 VPCs:

1. Create peering connection
2. Accept request
3. Update route tables
4. Test connectivity

---

## 🔬 Lab 5: Network ACLs

```bash
# Create NACL
aws ec2 create-network-acl \
  --vpc-id vpc-xxx

# Add inbound rule
aws ec2 create-network-acl-entry \
  --network-acl-id acl-xxx \
  --rule-number 100 \
  --protocol tcp \
  --port-range From=80,To=80 \
  --cidr-block 0.0.0.0/0 \
  --rule-action allow \
  --ingress
```

---

## ✅ Checklist

- [ ] Lab 1: VPC Design
- [ ] Lab 2: Security Groups
- [ ] Lab 3: ALB
- [ ] Lab 4: VPC Peering
- [ ] Lab 5: NACLs

---

**[← Back to README](./README.md)**
