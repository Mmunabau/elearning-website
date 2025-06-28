# 🧠 Automated Deployment of E-Learning Website

A fully static, globally available **e-learning website** hosted on AWS using **S3 and CloudFront**.  
Built using **HTML, CSS, JS**, deployed via **AWS CloudShell** and **AWS CLI**, and version-controlled with **Git & GitHub**.

👉 **Zero servers. Zero cost (Free Tier). High speed global delivery.**

---

## 📌 Architecture

![Architecture Diagram](assets/Architecture1-diagram.png)

---

## 💡 Features

- Responsive static site built with HTML, CSS, JS  
- Hosted on Amazon S3 (Static Website Hosting)  
- Delivered globally using CloudFront CDN  
- Enforced HTTPS and automatic HTTP-to-HTTPS redirection  
- Zero backend maintenance (100% static)  
- Version-controlled via Git and GitHub  
- Fully deployed from AWS CloudShell using AWS CLI  

---

## ⚙️ Step-by-Step Setup

### 1️⃣ Build Frontend Website

Structure:

```
elearning-site/
├── index.html
├── about.html
├── contact.html
└── assets/
    ├── css/
    ├── js/
    └── images/
```

📸 *Add screenshot of file structure*
![File structure](assets/file-structure.png)

---

### 2️⃣ Create and Configure S3 Bucket

- Create S3 bucket (e.g., `elearning-site-your name`)  
- Enable Static Website Hosting  
- Upload all files  
- Set index document: `index.html`  
- Make content public (adjust block settings + bucket policy)  

📸 *Add screenshot of S3 setup*
![S3 static hosting](assets/s3-setup-screenshot.png)

---

### 3️⃣ Deploy via AWS CLI

```bash
aws s3 cp . s3://elearning-site-your name/ --recursive
```

📸 *Screenshot: CloudShell upload*
![cli screenshot](assets/cli-screenshot.png)

---

### 4️⃣ Create CloudFront Distribution

- Set origin to `elearning-site-mm.s3-website-<region>.amazonaws.com`  
- Set Default Root Object: `index.html`  
- Enable “Redirect HTTP to HTTPS”  
- Deploy and wait for status `Deployed`  

📸 *Add screenshot of CloudFront setup*
![cloudfront](assets/cloudfront-screenshot.png)

---

### 5️⃣ Push Code to GitHub

```bash
git init
git remote add origin https://github.com/Mmunabau/elearning-website.git
git branch -M main
git add .
git commit -m "Initial commit - E-Learning Hub Website"
git push -u origin main
```

📸 *GitHub repo screenshot*
![GitHub](assets/github-screenshot.png)

---

### 5️⃣ 🔐 Create IAM Role for GitHub Actions (OIDC)
- Go to IAM > Identity providers > Add GitHub as OIDC provider
- Create a new IAM Role with trust policy for GitHub and attach policy:          
```bash
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:PutObject",
        "s3:DeleteObject",
        "cloudfront:CreateInvalidation"
      ],
      "Resource": "*"
    }
  ]
}

```

📸 *IAM  screenshot*
![IAM screenshot](assets/iam-screenshot.png)

---
### 5️⃣ ⚙️ Add GitHub Actions Workflow
- Create .github/workflows/deploy.yml in your project:          
```bash
name: Deploy to S3 and Invalidate CloudFront

on:
  push:
    branches:
      - main

permissions:
  id-token: write
  contents: read

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Configure AWS credentials
        uses: aws-actions/configure-aws-credentials@v4
        with:
          role-to-assume: arn:aws:iam::ACCOUNT_ID:role/github-deploy-role
          aws-region: us-east-1

      - name: Deploy to S3
        run: |
          aws s3 sync . s3://your-bucket-name --delete

      - name: Invalidate CloudFront
        run: |
          aws cloudfront create-invalidation --distribution-id YOUR_DIST_ID --paths "/*"


```

📸 *workflow screenshot*
![workflow](assets/workflow-screenshot.png)

---
### 3️⃣ 🚀 Push to Deploy

```bash
git add .
git commit -m "🚀 New deployment"
git push

```

📸 *Screenshot: CloudShell upload*
![sucess](assets/sucess-screenshot.png)

---

## 🚧 Challenges & Solutions

| Challenge                      | Solution                                                     |
|-------------------------------|--------------------------------------------------------------|
| 504 CloudFront error          | Used S3 **static site endpoint** instead of bucket name      |
| Git permission denied         | Used personal access token for HTTPS push                    |
| CloudShell file issues        | Corrected with `chmod` and reinitializing git folder         |
| Git history mismatch          | Merged with `--allow-unrelated-histories`                   |

---

## 📂 Repo Structure

```
elearning-site/
├── index.html
├── about.html
├── contact.html
├── assets/
│   ├── css/
│   │   └── style.css
│   ├── js/
│   │   └── script.js
│   └── images/
└── assets/
    ├── architecture-diagram.png
    ├── s3-setup-screenshot.png
    ├── cloudfront-setup-screenshot.png
    ├── github-deployment-screenshot.png
```

---

## 🧠 What I Learned

- Static website delivery with S3 and CloudFront  
- Using CloudShell for CLI-based deployment  
- Git/GitHub integration in real deployment projects  
- Troubleshooting permission and configuration issues in AWS

---

## 🌐 Final Hosted URL

🔗 `https://d3se3yb1ahhet4.cloudfront.net` *(Replace with your actual CloudFront domain)*

---

## 🤝 Let's Connect

📩 Muhammedmunabau@gmail.com  
🔗 [linkedin.com/in/ameen123](https://linkedin.com/in/ameen123)  
#AWS #WebHosting #CloudFront #S3 #CloudProjects  




