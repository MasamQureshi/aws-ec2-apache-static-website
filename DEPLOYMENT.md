# Deployment Guide

## Project

AWS EC2 Apache Static Website Deployment

---

# Prerequisites

Before deployment, ensure you have:

- AWS Account
- EC2 Ubuntu Instance
- SSH Key Pair (.pem)
- Git (Optional)
- Internet Connection

---

# Step 1: Launch an EC2 Instance

1. Sign in to the AWS Management Console.
2. Navigate to **EC2 Dashboard**.
3. Click **Launch Instance**.
4. Select **Ubuntu Server**.
5. Choose an instance type (e.g., `t2.micro` for Free Tier).
6. Create or select an existing Key Pair.
7. Configure the Security Group.

Allow the following inbound rules:

| Type | Port | Source |
|------|------|--------|
| SSH | 22 | 0.0.0.0/0 |
| HTTP | 80 | 0.0.0.0/0 |

Launch the instance.

---

# Step 2: Connect to the EC2 Instance

From your terminal:

```bash
ssh -i your-key.pem ubuntu@YOUR_PUBLIC_IP
```

Example:

```bash
ssh -i my-key.pem ubuntu@34.xxx.xxx.xxx
```

---

# Step 3: Update the System

```bash
sudo apt update
sudo apt upgrade -y
```

---

# Step 4: Install Apache2

```bash
sudo apt install apache2 -y
```

Verify installation:

```bash
sudo systemctl status apache2
```

If Apache is not running:

```bash
sudo systemctl start apache2
```

Enable Apache to start automatically after reboot:

```bash
sudo systemctl enable apache2
```

---

# Step 5: Verify Apache Installation

Open the default Apache page:

```
http://YOUR_PUBLIC_IP
```

You should see the Apache default webpage.

---

# Step 6: Remove the Default Website

```bash
sudo rm -f /var/www/html/index.html
```

---

# Step 7: Deploy Website Files

Navigate to your project directory.

Example:

```bash
cd ~/2166_ivory_flow
```

Copy the website files:

```bash
sudo cp -r * /var/www/html/
```

Verify:

```bash
ls /var/www/html
```

---

# Step 8: Restart Apache

```bash
sudo systemctl restart apache2
```

---

# Step 9: Verify the Website

Visit:

```
http://YOUR_PUBLIC_IP
```

The deployed website should now be accessible.

---

# Verification Commands

## Check Apache Status

```bash
sudo systemctl status apache2
```

---

## Check Listening Ports

```bash
sudo ss -tlnp | grep :80
```

Expected output:

```
LISTEN 0 511 *:80 *:*
```

---

## Check Firewall Status

```bash
sudo ufw status
```

Expected output:

```
Status: inactive
```

or ensure that HTTP (port 80) is allowed if UFW is enabled.

---

## Verify Website Files

```bash
ls -lah /var/www/html
```

---

# Troubleshooting

## Apache Service Not Running

Start Apache:

```bash
sudo systemctl start apache2
```

Restart Apache:

```bash
sudo systemctl restart apache2
```

---

## Website Not Loading

Check:

- Apache service is running.
- Security Group allows HTTP (port 80).
- Public IPv4 address is correct.
- Website files are present in `/var/www/html`.

---

## Permission Issues

Set proper ownership:

```bash
sudo chown -R www-data:www-data /var/www/html
```

Set permissions:

```bash
sudo chmod -R 755 /var/www/html
```

---

# Security Group Configuration

Ensure the following inbound rules are configured:

| Service | Port | Source |
|----------|------|--------|
| SSH | 22 | 0.0.0.0/0 |
| HTTP | 80 | 0.0.0.0/0 |

---

# Project Outcome

After completing these steps:

- Ubuntu server is running on AWS EC2.
- Apache2 is installed and configured.
- Static website is deployed.
- Website is publicly accessible over HTTP.
- Deployment is managed using Linux commands and AWS services.

---

# Future Improvements

- Configure HTTPS using Let's Encrypt.
- Attach an Elastic IP to avoid IP changes.
- Connect a custom domain.
- Containerize the application with Docker.
- Automate deployments using GitHub Actions.
- Provision infrastructure using Terraform.

---

# Author

**Masam Hussain Qureshi**

Aspiring DevOps Engineer

GitHub: https://github.com/MasamQureshi
