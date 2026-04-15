# 🚀 WordPress Hosting on AWS (EC2 + RDS with LAMP Stack)

## 📌 Project Overview

This project demonstrates the deployment of a **WordPress website on AWS Cloud** using a **LAMP stack (Linux, Apache, PHP)** on EC2 and a **managed MySQL database on Amazon RDS**.

The architecture separates the application and database layers, making the system more **scalable, secure, and production-ready**.

---

## 🧠 Architecture Diagram

```
User (Browser)
      ↓
EC2 Instance (Apache + PHP)
      ↓
Amazon RDS (MySQL Database)
```

---

## 🏗️ Architecture Explanation

* **EC2 Instance** hosts the WordPress application using Apache and PHP.
* **Amazon RDS** handles the MySQL database separately.
* Communication between EC2 and RDS is secured using **Security Groups**.
* This setup improves:

  * Scalability
  * Security
  * Maintainability

---

## ⚙️ Tech Stack

* ☁️ AWS EC2 (Amazon Linux)
* 🗄️ AWS RDS (MySQL)
* 🌐 Apache Web Server
* 🐘 PHP
* 📝 WordPress

---

## ✨ Features

* Deploy WordPress on AWS Cloud
* Use managed database (RDS)
* Configure LAMP stack on EC2
* Secure communication via Security Groups
* Real-world cloud architecture implementation

---

## 🚀 Deployment Steps

### 🔹 Step 1: Launch EC2 Instance

* Go to AWS Console → EC2 → Launch Instance
* Choose:

  * AMI: Amazon Linux (2023 / 2)
  * Instance Type: t2.micro (Free tier)
* Configure Security Group:

  * Allow SSH (22)
  * Allow HTTP (80)
  * Allow HTTPS (443)
    

---

### 🔹 Step 2: Connect to EC2

```bash
ssh -i your-key.pem ec2-user@your-public-ip
```

---

### 🔹 Step 3: Install LAMP Stack

```bash
sudo dnf update -y
sudo dnf install httpd php php-mysqlnd -y
```

Start Apache:

```bash
sudo systemctl start httpd
sudo systemctl enable httpd
```

---

### 🔹 Step 4: Create RDS Database

* Go to AWS → RDS → Create Database
* Engine: MySQL
* Template: Free tier

Set:

* DB Name: wordpressdb
* Username: admin
* Password: your-password

⚠️ Important:

* Enable Public Access (only for testing)
* Allow inbound rule:

  * Port 3306 (MySQL)
  * Source: EC2 Security Group

---

### 🔹 Step 5: Connect EC2 to RDS

Install MySQL client:

```bash
sudo dnf install mariadb105 -y
```

Connect:

```bash
mysql -h your-rds-endpoint -u admin -p
```

---

### 🔹 Step 6: Install WordPress

```bash
cd /var/www/html
sudo wget https://wordpress.org/latest.tar.gz
sudo tar -xzf latest.tar.gz
sudo cp -r wordpress/* .
```

---

### 🔹 Step 7: Set Permissions

```bash
sudo chown -R apache:apache /var/www/html
sudo chmod -R 755 /var/www/html
```

---

### 🔹 Step 8: Configure WordPress

```bash
cd /var/www/html
sudo cp wp-config-sample.php wp-config.php
sudo nano wp-config.php
```

Update database configuration:

```php
define('DB_NAME', 'wordpressdb');
define('DB_USER', 'admin');
define('DB_PASSWORD', 'your-password');
define('DB_HOST', 'your-rds-endpoint');
```

---

### 🔹 Step 9: Access Website

Open browser:

```
http://your-ec2-public-ip
```

* Complete WordPress setup
* Create admin user
* Launch your website 🎉

---

## 🔐 Security Best Practices

* Disable public access for RDS in production
* Use private subnet for database
* Enable HTTPS (SSL certificate)
* Use strong passwords
* Regular database backups

---

## 📸 Screenshots

*Add screenshots of your project here*

Example:

* EC2 Instance running
* RDS Database dashboard
* WordPress homepage

---

## 📊 Future Enhancements

* 🔁 Load Balancer (Elastic Load Balancer)
* 📈 Auto Scaling Group
* 🌍 CloudFront CDN
* 🌐 Custom Domain with Route 53
* 🔒 HTTPS with Let's Encrypt

---

## 🧪 Testing

* Verified Apache server is running
* Successfully connected EC2 to RDS
* WordPress installed and configured
* Website accessible via public IP

---

## 🐞 Common Issues & Fixes

### ❌ Error: "Error Establishing Database Connection"

✔ Check:

* RDS endpoint is correct
* Security group allows EC2
* Database credentials are correct

---

### ❌ Apache Not Starting

```bash
sudo systemctl status httpd
```

---

### ❌ Permission Issues

```bash
sudo chown -R apache:apache /var/www/html
```

-<img width="1920" height="853" alt="Screenshot 2026-04-14 192936" src="https://github.com/user-attachments/assets/b563079c-60a3-4d77-82c8-ddf41ea648cf" />
<img width="1920" height="848" alt="Screenshot 2026-04-14 192800" src="https://github.com/user-attachments/assets/a3bd1f8c-39b0-4324-81bf-1032d04998e5" />
<img width="1920" height="1020" alt="Screenshot 2026-04-14 194230" src="https://github.com/user-attachments/assets/6e0288bd-4380-443e-8e3c-e31d4550746f" />
<img width="1920" height="1020" alt="Screenshot 2026-04-14 185841" src="https://github.com/user-attachments/assets/77ec1e8f-930b-4617-aa2c-9271d77e4ee1" />
<img width="1920" height="1020" alt="Screenshot 2026-04-14 190934" src="https://github.com/user-attachments/assets/d16a4322-0834-4150-85ed-96565aec5be1" />
<img width="1920" height="1020" alt="Screenshot 2026-04-14 191106" src="https://github.com/user-attachments/assets/63fd1490-30a9-4f0f-b7de-0a49daffd9df" />






