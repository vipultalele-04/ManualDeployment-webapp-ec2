# Manual Deployment of Web App on AWS EC2

A React web application manually deployed on an AWS EC2 instance — no containers, no orchestration, just raw server setup and deployment.

🔗 **Live Demo:** [http://43.204.32.94:3000/](http://43.204.32.94:3000/)

---

## Tech Stack

- **Clone:** GitHub
- **Hosting:** AWS EC2 (Ubuntu)
- **Runtime:** Node.js
- **Reverse Proxy:** NGINX (port 3000)
- **Process manager — keeps app alive:** PM2
---


## Local Setup

**Prerequisites:** Node.js 14+, npm

```bash
# Clone the repo
git clone https://github.com/vipultalele-04/ManualDeployment-webapp-ec2.git
cd ManualDeployment-webapp-ec2

# Install dependencies
npm install

#Start the application
node index.js & 
```

---

## AWS EC2 Manual Deployment Steps

### 1. Launch EC2 Instance
- AMI: Ubuntu 22.04 LTS
- Instance type: t2.micro (free tier)
- Add security group

### 2. Security group configuration

Configured Security Group inbound rules:
Port 22 (SSH) — for remote access

Port 80 (HTTP) — for web traffic

Port 3000 (Node.js) — for direct app access

port 443 (HTTPS) - for secure web traffic(SSL/TLS)

### 3. Connect to EC2

```bash
ssh -i your-key.pem ubuntu@<EC2_PUBLIC_IP>
```

### 4. Clone & Run the App

```bash
git clone https://github.com/vipultalele-04/ManualDeployment-webapp-ec2.git
cd ManualDeployment-webapp-ec2
npm install
node index.js &
```

### 5. Keep App Running (optional)

```bash
# Install pm2 to keep app alive after SSH disconnect
sudo npm install -g pm2
pm2 start "npm start" --name webapp
pm2 save
```

### 6. Access Your Application

Visit http://your-ec2-public-ip:port in a browser.
---

