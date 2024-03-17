---
title: "Terrafrom module for creating VMs on AWS"
draft: false
date: 2024-03-16T09:16:45.000Z
description: "Created and published terraform module."
---

## Introduction

I often find myself creating servers for testing and development purposes on AWS. I have used terraform for some time, but the script was not in a terraform module, so I created one and published it on the terraform registry. The module is available here:

I know similar modules already exist, but those modules assume you have a VPC and other networking resources already in place. This module creates everything from scratch, including a VPC, a subnet, a security group, and an EC2 instance. Because of that is not that flexible, but it's perfect for my use case.

Terraform registry link: https://registry.terraform.io/modules/defilippomattia/zero-to-ec2/aws/latest

GitHub repository link: https://github.com/defilippomattia/terraform-aws-zero-to-ec2
