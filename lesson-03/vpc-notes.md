# Lesson 3: VPC Fundamentals

## What I built (region: ap-south-1, Mumbai)
- VPC: sidd-lab-vpc, CIDR 10.0.0.0/16
- 2 public subnets (10.0.1.0/24, 10.0.2.0/24) across two Availability Zones
- 2 private subnets (10.0.11.0/24, 10.0.12.0/24) across two Availability Zones
- Internet Gateway: sidd-igw, attached to the VPC
- Public route table: 0.0.0.0/0 -> Internet Gateway, associated with the public subnets
- Private route table: local route only, associated with the private subnets

## Key concepts
- A subnet is public only because its route table sends 0.0.0.0/0 to an Internet Gateway
- Private subnets have no route to the internet; resources there stay unreachable from outside
- Every route table has a local route so resources inside the VPC can talk to each other
- Two Availability Zones give resilience if one data center fails
- The default VPC was left untouched

## Next
- Security Groups vs Network ACLs
- NAT Gateway for outbound access from private subnets
- Launch an EC2 instance in a public subnet and connect with SSH

## Security Groups vs Network ACLs
- Security Group: instance level, stateful, allow rules only
- NACL: subnet level, stateless, allow and deny rules, evaluated by rule number
- Because NACLs are stateless, return traffic needs an explicit rule (ephemeral ports 1024-65535)
- Created sidd-web-sg: SSH from my IP, HTTP from anywhere
- Created sidd-db-sg: MySQL (3306) allowed only from sidd-web-sg (security group reference)
- Created sidd-public-nacl with explicit allow rules; not yet associated with a subnet
- Never open SSH to 0.0.0.0/0