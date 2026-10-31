# AWS VPC Peering Lab

## Overview

This repository contains a **complete, reproducible** AWS VPC peering lab implemented with **Terraform**. It builds two VPCs, a bastion host, two private application servers, a VPC peering connection, the required route tables, and security groups. The lab also provides scripts for:

* Prerequisite checks (Terraform, AWS CLI, credentials)
* Infrastructure validation (`terraform fmt`, `terraform validate`)
* Planning & applying the infrastructure
* Connectivity testing (baseline failure, successful ping, SSH via ProxyJump, controlled ICMP failure/recovery)
* Cleanup of all resources

All resources are tagged with `Project = EWB-VPC-Peering` to make cleanup easy.

## Directory Layout

```
aws-vpc-peering-project/
├─ README.md                     <-- This file
├─ .gitignore                    <-- Git ignore rules
├─ architecture/
│   ├─ architecture.md           <-- Narrative architecture description
│   └─ architecture-diagram.mmd  <-- Mermaid diagram source
├─ terraform/
│   ├─ main.tf                   <-- Core infrastructure resources
│   ├─ variables.tf              <-- Input variables
│   ├─ outputs.tf                <-- Useful outputs (IPs, IDs)
│   └─ provider.tf               <-- Provider configuration
├─ scripts/
│   ├─ prereq_check.ps1         <-- Windows PowerShell checks
│   ├─ validate.ps1              <-- Terraform validation
│   ├─ plan.ps1                  <-- Terraform plan
│   ├─ apply.ps1                 <-- Terraform apply (with approval)
│   ├─ destroy.ps1               <-- Terraform destroy
│   ├─ connectivity_test.ps1     <-- Automated ping/SSH tests
│   └─ icmp_failure_test.ps1    <-- Controlled ICMP rule removal/recovery
└─ docs/
    ├─ implementation_guide.md   <-- Step‑by‑step deployment guide
    ├─ troubleshooting_guide.md   <-- Common issues & fixes
    ├─ viva_q_and_a.md            <-- Expected viva questions & answers
    └─ final_report_template.md    <-- Report template for submission
```

## Prerequisites

* **Terraform 1.6+** – download from https://developer.hashicorp.com/terraform/downloads
* **AWS CLI v2** – `aws --version`
* **AWS credentials** configured (`aws configure`) with permissions to create VPCs, EC2, IAM, and related resources.
* **OpenSSH** (Windows 10+ includes it) for the bastion ProxyJump configuration.
* **PowerShell 5+** – all helper scripts are PowerShell‑compatible.

Refer to `docs/implementation_guide.md` for detailed setup instructions.
```
