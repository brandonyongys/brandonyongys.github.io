---
layout: post
title: Connecting to RDS DB with SSH Tunnel / Hosting a Database: From EC2 to RDS with an SSH Tunnel
description: What is I'm not satisfied?
date: 2025-03-25
tags: [career, life, growth]

comments: true
published: true

---

Previously, I hosted my own database on an EC2 instance, but maintaining it manually became too much overhead - especially when all I needed was a simple way to store and retrieve data for downstream applications.

To simplify management, I switched to Amazon RDS. While RDS can be more expensive than self-hosting on EC2, it offers managed services, backups, and ease of use. Plus, AWS provides low-cost and free-tier instances, which is perfect for my use case with minimal resource requirements.

For my setup, I chose PostgreSQL as it is lightweight, open-source, and widely supported (MySQL is another viable alternative). The database is deployed within a private subnet and secured via a specific security group.

⚠️ Reminder: If you opt to auto-generate your database password during setup, be sure to save it for future access.

# Setting Up an EC2 Bastion Host
Since my RDS database resides in a private subnet, I cannot access it directly. To connect securely, I set up an SSH tunnel using a bastion host. The architecture is illustrated below:

![Overall_architecture](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/assets/img/2025-imgs/rds-ssh.png)

I launched an Ubuntu EC2 instance in the public subnet of the same VPC and attached the same security group as my database. This instance is used solely as a bastion host, so I chose a small instance type to minimize costs.

Key Considerations:
1. Key Pair:
    * When creating the EC2 instance, generate a key pair (which will be your .pem file).
    * This .pem file is required to establish an SSH tunnel later.

1. Security Group Rules:
    * Allow SSH (port 22) connection only from your IP.
    * Permit connection from the EC2 instance to the PostgreSQL database on port 5432 using its private IP.


# Connecting to RDS from a Local Machine via SSH Tunnel
To access my RDS PostgreSQL database, I establish an SSH tunnel from my local machine:
```
ssh -i /path/to/your-key.pem -L 5432:<rds_endpoint>:5432 <username>@<ec2_public_IPv4_DNS>
```

If the connection is successful, you will be logged into your Ubuntu instance and can navigate around.

# Configuring DBeaver for RDS Access
Since I use DBeaver as my database interface, I configure it as follows:
* __Server host:__ RDS Endpoint
* __Server username and password:__ RDS credentials
* __SSH host:__ EC2 Public IPv4 DNS
* __SSH username:__ EC2 instance username
* __SSH authentication:__ Public Key
* __SSH private key:__ your-key.pem


With that, my RDS PostgreSQL database is now accessible via DBeaver, allowing me to interact with it freely on my local machine.

This setup enables a secure and scalable database connection without exposing RDS to the public internet. 🚀

