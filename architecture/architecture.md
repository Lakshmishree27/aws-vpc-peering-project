# Architecture Overview

The lab consists of two isolated VPCs that are connected via **VPC Peering**.

* **VPC A** – `ewb-vpc-a` (CIDR `10.10.0.0/16`)
  * Public subnet `ewb-a-public` (`10.10.1.0/24`) – hosts the bastion.
  * Private subnet `ewb-a-private` (`10.10.2.0/24`) – hosts **App‑A**.
* **VPC B** – `ewb-vpc-b` (CIDR `10.20.0.0/16`)
  * Private subnet `ewb-b-private` (`10.20.1.0/24`) – hosts **App‑B**.

Both VPCs are in the same AWS account and region (`ap‑south‑1`).

A **single bastion host** lives in the public subnet of VPC A and is the only instance with a public IPv4 address. All administrative SSH traffic to the private application servers must traverse this bastion using an SSH `ProxyJump` configuration.

The required AWS resources are:

* VPCs, subnets, Internet Gateway, VPC peering, route tables & associations.
* Security groups with the exact inbound rules described in the workbook.
* Three EC2 instances (bastion, App‑A, App‑B) using Amazon Linux 2023 and the key pair `ewb-lab`.
* Tags `Project = EWB-VPC-Peering` and `Student = <your‑name>` for easy cleanup.

All networking rules, routes, and security‑group settings are deliberately minimal (least‑privilege) to satisfy the lab’s demonstration objectives while keeping the attack surface low.
