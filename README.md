# AWS EC2 Apache Static Website Deployment

## 📌 Project Overview

This project demonstrates how to deploy a responsive static website on an Amazon EC2 Ubuntu instance using the Apache2 web server.

The goal of this project was to gain hands-on experience with Linux administration, AWS cloud services, Apache web server configuration, Git, GitHub, and website deployment.

---

## 🚀 Features

- Responsive static website
- Hosted on AWS EC2
- Apache2 Web Server
- Publicly accessible over HTTP
- Linux server administration
- Git & GitHub version control

---

## 🛠 Technologies Used

- Amazon Web Services (AWS EC2)
- Ubuntu Linux
- Apache2
- HTML5
- CSS3
- JavaScript
- Git
- GitHub

---

## 📁 Project Structure

```
aws-ec2-apache-static-website/
│
├── images/
├── index.html
├── timer.html
├── tooplate-ivory-style.css
├── tooplate-ivory-script.js
├── README.md
├── DEPLOYMENT.md
└──ARCHITECTURE.md
 
```

## ⚙️ Deployment Steps

### 1. Launch an Ubuntu EC2 Instance

- Launch an Ubuntu EC2 instance from AWS.
- Configure the Security Group to allow:
  - SSH (22)
  - HTTP (80)

---

### 2. Connect to the Instance

```bash
ssh -i your-key.pem ubuntu@YOUR_PUBLIC_IP
```

---

### 3. Update Packages

```bash
sudo apt update
```

---

### 4. Install Apache2

```bash
sudo apt install apache2 -y
```

---

### 5. Verify Apache

```bash
sudo systemctl status apache2
```

---

### 6. Deploy Website Files

```bash
sudo cp -r * /var/www/html/
```

---

### 7. Restart Apache

```bash
sudo systemctl restart apache2
```

---

### 8. Verify Website

Open your browser and visit:

```
http://YOUR_PUBLIC_IP
```

---

## ✅ Verification Commands

Check Apache status:

```bash
sudo systemctl status apache2
```

Check if Apache is listening on Port 80:

```bash
sudo ss -tlnp | grep :80
```

Check firewall status:

```bash
sudo ufw status
```


## 🏗 Architecture

```
                Internet
                     │
                     ▼
           AWS Security Group
             HTTP (Port 80)
                     │
                     ▼
          Ubuntu EC2 Instance
                     │
                     ▼
              Apache2 Web Server
                     │
                     ▼
            /var/www/html
                     │
                     ▼
             Static Website
```

---

## 📚 What I Learned

During this project, I learned how to:

- Launch and manage AWS EC2 instances
- Configure Security Groups
- Connect to Linux servers using SSH
- Install and configure Apache2
- Deploy static websites
- Manage files using Linux commands
- Use Git for version control
- Push projects to GitHub using SSH authentication
- Troubleshoot deployment and networking issues

---

## 🔮 Future Improvements

- Add HTTPS using Let's Encrypt
- Connect a custom domain
- Containerize the application using Docker
- Automate deployment with GitHub Actions
- Provision infrastructure using Terraform

---

## 👨‍💻 Author

**Masam Hussain Qureshi**

Aspiring DevOps Engineer

GitHub: https://github.com/MasamQureshi

---

## ⭐ If you like this project

If you found this project helpful, feel free to ⭐ star the repository.
