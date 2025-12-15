## :zap: Launching an NGINX Web Server on an Amazon EC2 Instance:

I will be highlighting the steps to launch an NGINX web server on an Amazon EC2 instance, and map it to a domain purchased through Cloudflare.

---

## Step 1: Purchase a Domain on Cloudflare

This should cost around $5 - $15.

---

## Step 2: Launch an EC2 Instance on AWS
- AMI: Amazon Linux 2023
- Instance Type: t3.micro
- Security Group Inbound Rules:
  - Port 22 (SSH) – Your IP
  - Port 80 (HTTP) – 0.0.0.0/0
  - Port 443 (HTTPS) – 0.0.0.0/0

 Note: SSH access was temporarily opened for troubleshooting due to dynamic IP changes, then re-restricted to a single IP.
 
---

## Step 3: Note the Public IPv4 Address

After launching, locate the **Public IPv4 address** in the **EC2 instance summary**.  
You'll use this later to point your domain (on Cloudflare A record settings) to the server.

---

## Step 4: Connect to the EC2 Instance to open up AWS Linux 

---

## Step 5: Install NGINX

Run these commands in your terminal:

```bash
sudo yum update -y
sudo yum install -y nginx
sudo systemctl start nginx
sudo systemctl enable nginx
```
---

## Step 6: Login to your Cloudfare account, and create an A record for your domain. Point this to the Public IPV4 address you noted down earlier

Note: Proxy Status was toggled off to prevent Error 522 from occuring. This isolated the issue by testing direct EC2 IP access. Resolved by adjusting DNS proxy settings and security group rules

---

## Step 7: Go back onto the terminal, and confirm propagation

Run this command: 

```bash
nslookup <Your domain>
```

After a few minutes, the result should show the public IPV4 address, with your domain:

---

## Step 8: Customise your page with the command

Run this command:

```bash
sudo yum install nginx -y sudo systemctl start nginx
```
---

## Step 9: Finally, search your domain on your browser and you should find your website

---

# You now have an NGINX web server running on EC2, mapped to your custom domain!
