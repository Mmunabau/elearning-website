# 🧠 Automated Deployment of E-Learning Website

A fully static, globally available **e-learning website** hosted on AWS using **S3 and CloudFront**.  
Built using **HTML, CSS, JS**, deployed via **AWS CloudShell** and **AWS CLI**, and version-controlled with **Git & GitHub**.

👉 **Zero servers. Zero cost (Free Tier). High speed global delivery.**

---

## 📌 Architecture

![Architecture Diagram](assets/architecture-diagram.png)

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

---

### 2️⃣ Create and Configure S3 Bucket

- Create S3 bucket (e.g., `elearning-site-mm`)  
- Enable Static Website Hosting  
- Upload all files  
- Set index document: `index.html`  
- Make content public (adjust block settings + bucket policy)  

📸 *Add screenshot of S3 setup*

---

### 3️⃣ Deploy via AWS CLI

```bash
aws s3 cp . s3://elearning-site-mm/ --recursive
```

📸 *Screenshot: CloudShell upload*

---

### 4️⃣ Create CloudFront Distribution

- Set origin to `elearning-site-mm.s3-website-<region>.amazonaws.com`  
- Set Default Root Object: `index.html`  
- Enable “Redirect HTTP to HTTPS”  
- Deploy and wait for status `Deployed`  

📸 *Add screenshot of CloudFront setup*

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




