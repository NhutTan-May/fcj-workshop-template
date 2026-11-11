---
title: "Blog 3"
date: 2026-11-05
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# AWS ACCOUNT ACCESS MANAGER: CENTRALIZED WORKFORCE ACCESS WITH IAM ROLE FLEXIBILITY

AWS recently announced **AWS Account Access Manager (AAM)**, a new AWS IAM capability that bridges centralized workforce access administration in AWS IAM Identity Center with the granular flexibility of local IAM roles inside individual AWS accounts. It eliminates the long-standing trade-off between centralized Permission Sets (which can be rigid to customize per account) and manually maintaining custom federation setups, enabling organizations to govern multi-account access consistently at scale.

Key points to know:

- **Direct IAM Role mapping from a centralized directory:** Integrates with an organization instance of **AWS IAM Identity Center** (synced with users and groups from corporate IdPs such as Okta, Ping Identity, Cisco Duo, or Microsoft Entra ID), allowing administrators to assign existing account-level IAM roles to users and groups from a single management view.
- **Preserves full native IAM Role capabilities:** Retains all native IAM role features including custom trust policies, role paths, attribute-based access control (ABAC), and IAM role tags for cost allocation.
- **Autonomy for builders with centralized governance:** Application and workload teams remain free to author and tune IAM roles to fit project-specific requirements, while security and platform teams maintain central visibility and control across the entire AWS Organization.
- **User-level audit attribution and multi-channel sign-in:** Uses *trusted identity propagation* to carry individual user context into assumed role sessions, ensuring **AWS CloudTrail** logs pinpoint the exact human identity behind every action rather than just a generic role name; supports login via Account Access Portal, AWS Access Portal, or AWS CLI (`aws login`).
- **Coexists smoothly with Permission Sets:** No big-bang migration is required—organizations can use Account Access Manager in accounts that need specialized IAM role configurations while keeping existing Permission Sets elsewhere.
- **IaC automation at no extra charge:** Supports provisioning and scaling via AWS CloudFormation, AWS CLI, Terraform, and Pulumi, and is available at **no additional cost** (you only pay for underlying AWS resources) across AWS Commercial Regions.

This feature is especially useful for multi-account AWS environments where security teams need centralized governance and user-level auditing without slowing down engineering teams configuring fine-grained application permissions.

**Image:**

![AWS Account Access Manager Architecture](/fcj-workshop-template/images/3-Blog/Blog03.jpg)

**Link:**
- 
