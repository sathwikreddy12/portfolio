# AWS Static Portfolio Website (S3 + CloudFront)

## 📌 Project Overview

This project demonstrates hosting a **static portfolio website** on **Amazon S3** and delivering it globally using **Amazon CloudFront**.  
The website is built using **HTML and CSS**, version-controlled with **Git/GitHub**, and follows best practices for **static website hosting, secure access, and CDN delivery**.

---

## 📂 Project Structure

portfolio/
├── index.html
├── styles.css
├── assets/ # Images and media files
└── README.md

yaml
Copy code

---

## 🚀 Deployment Steps

### 1️⃣ Website Development
* Created a responsive static portfolio using HTML and CSS
* Verified locally by opening `index.html` in a browser

### 2️⃣ Version Control (Git & GitHub)
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin <GitHub_Repo_URL>
git push -u origin main
3️⃣ Upload to Amazon S3
Created an S3 bucket with a unique name

Enabled Static Website Hosting

Set index.html as the default root object

Uploaded files using CLI:

bash
Copy code
aws s3 cp ./portfolio s3://<bucket-name>/ --recursive
4️⃣ Configure Bucket Policy
Disabled Block Public Access

Added the following policy to allow public read access:

json
Copy code
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::<sathwik-portfolio-2026>/*"
    }
  ]
}
Verified website via S3 endpoint:

http://sathwik-portfolio-2026.s3-website.us-east-2.amazonaws.com/
5️⃣ Configure CloudFront
Created a CloudFront distribution with the S3 website as origin

Enabled HTTPS using the default CloudFront TLS certificate

Enabled HTTP → HTTPS redirection

Verified the live website via CloudFront URL

📄 Deliverables
GitHub Repository
Link: https://github.com/sathwikreddy12/portfolio

Hosted Website URL
S3 URL: http://sathwik-portfolio-2026.s3-website.us-east-2.amazonaws.com/

Screenshots (Optional)

S3 Bucket policy & configuration

Live website

README.md
Explains project structure, deployment steps, commands, and architecture (this file)


🔐 Security & Best Practices
HTTPS enabled via CloudFront TLS certificate

Public access limited to s3:GetObject

No backend or sensitive data exposed

Minimal permissions following AWS best practices

💡 Key Learnings
Difference between S3 API endpoint and S3 website endpoint

Importance of CDN for global performance and security

Real-world AWS deployment workflow

Cost-efficient cloud architecture

👤 Author
Sathwik Reddy – DevOps & Data Engineering Enthusiast
