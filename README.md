# 🌐 E-Learning Hub Website

A responsive, animated e-learning website built with HTML, CSS, JavaScript, and hosted on **AWS S3** with **CloudFront CDN**. Designed to showcase cloud deployment for frontend projects.

![Demo Screenshot](assets/images/elearning-preview.png)

---

## 🔗 Live Demo

👉 [Visit Live Site](https://d3se3yb1ahhet4.cloudfront.net)

---

## 📦 Features

- 🎨 Clean and modern UI with animation
- 📱 Responsive layout for mobile and desktop
- 📚 Three learning categories: Web Development, Cloud, and Data Science
- 📄 Multiple pages: Home, About, Contact
- 🌍 Deployed globally via AWS S3 + CloudFront

---

## 🧠 Technologies Used

| Tech           | Purpose                         |
|----------------|----------------------------------|
| **HTML5**      | Page structure                   |
| **CSS3**       | Styling and animations           |
| **JavaScript** | Interactivity                    |
| **AWS S3**     | Static website hosting           |
| **AWS CloudFront** | CDN and HTTPS performance boost |

---

## 🗂️ Folder Structure

elearning-site/
├── index.html
├── about.html
├── contact.html
└── assets/
├── css/
│ └── style.css
├── js/
│ └── script.js
└── images/

---

## 🚀 Deployment Steps

| Step | Action |
|------|--------|
| ✅ 1 | Created S3 bucket `elearning-site-mm` and enabled **static website hosting** |
| ✅ 2 | Uploaded all files: `index.html`, `about.html`, `contact.html`, and `assets/` |
| ✅ 3 | Made the bucket content **publicly accessible** |
| ✅ 4 | Created **CloudFront distribution** pointing to the S3 static website endpoint |
| ✅ 5 | Enabled "Redirect HTTP to HTTPS" and set default root to `index.html` |
| ✅ 6 | Deployed and tested the site at CloudFront domain |

---

## ⚠️ Challenges & Solutions

| Challenge | Solution |
|----------|----------|
| 504 Gateway Timeout from CloudFront | Used the correct **S3 static website endpoint**, not the REST endpoint |
| Permission errors in CloudShell | Reset folder permissions using `chmod` |
| Git push errors due to repo mismatch | Pulled remote `main` branch with `--allow-unrelated-histories` |
| Token not pasting | Manually typed the token into GitHub auth prompt |
| Missing root object in CloudFront | Added `index.html` in **behavior settings** after creation |

---

## 🧪 Local Testing

Before deploying, test locally by opening `index.html` in the browser or using a local server like:

```bash
npx serve .


📌 GitHub Repo
🔗 https://github.com/Mmunabau/elearning-website

✍️ Author
Muhammed Ameen Munabau
Cloud | Web | AI Enthusiast 🌍
LinkedIn • GitHub




