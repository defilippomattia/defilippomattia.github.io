---
title: "I created fakeiotapi.xyz"
draft: false
date: 2023-09-04T09:16:45.000Z
description: "Pseudo-real IoT data provided by a free REST API."
---

## Introduction

I created a fake IoT API that provides pseudo-real IoT data. It's available at [fakeiotapi.xyz](https://fakeiotapi.xyz/).

This was mostly done for me to learn deployment of a full stack application on AWS so the actual frontend and backend code is simple and probably not following best practices.

## Application

The application is created with Go, React, PostgreSQL and nginx, all running as Docker containers on a single EC2 instance. Certificates are created using Let's Encrypt and Certbot.

{{< img src="application-diagram.png" alt="application diagram">}}

## Deployment diagram

The application is hosted on a single EC2 instance, so deployment is very basic.

Whole infrastructure (VPC, subnet, DNS stuff, EC2 instance etc.) is created using Terraform.

{{< img src="deployment-diagram.png" alt="deployment diagram">}}

## GitHub CI/CD

I used GitHub Actions to automatically deploy the application on every push to the main branch.

On every push to the main branch, GitHub Actions will:

1. Run integration tests (tests that the GO API is working correctly)

2. Sync the code from repository to EC2 instance (using rsync)

3. Build and deploy the application (using docker-compose)

## Conclusion

Some improvements that could be done:

- Deploy using ECS instead of EC2
- Automate certificate creation (and renewal)
