---
title : "Frontend-S3"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

In this module, we will deploy the Web interface (React/Next.js) of the WeDo Workspace project to the Internet environment. We will store the static website on **Amazon S3** and use **Amazon CloudFront** for high-speed distribution, while also protecting the system with a WAF firewall.

### 5.6.1. Build Frontend Source Code
First, you need to compile the React source code into static files.
* Open the Terminal in the folder containing the Frontend code.
* Ensure that the environment variable `.env` points to the API Endpoint of the Application Load Balancer (ALB).
* Run: `npm run build`.
* The result we obtained is the directory. `dist` Contains an optimized compressed interface.
![Build Source Code Frontend](/fcj-workshop-template/images/5-Workshop/5.6-Frontend-S3/frontend-build.jpg)

### 5.6.2. Create an S3 Bucket and Upload Web
* Access **AWS Console** → **S3** → **Create bucket**.
* Bucket name: `wedo-frontend-2026`.
* Uncheck **Block all public access** (to enable public web access or easy access via CloudFront).
* Click **Create bucket**.
![Create S3 Bucket](/fcj-workshop-template/images/5-Workshop/5.6-Frontend-S3/s3-create.jpg)

* Open the newly created bucket, click the **Upload** button, and drag and drop all the contents of the `dist` folder onto S3.
![Upload Frontend go up S3](/fcj-workshop-template/images/5-Workshop/5.6-Frontend-S3/s3-upload-success.png)

### 5.6.3. Grant permissions & Activate Static Website Hosting
* Switch to the **Permissions** tab → Scroll down to the **Bucket policy** section → **Edit**.
* Dán Policy allows `s3:GetObject` to have permission to read Public files:
![Update S3 Bucket Policy](/fcj-workshop-template/images/5-Workshop/5.6-Frontend-S3/s3-policy.png)

* Continue to the **Properties** tab → Scroll down to the **Static website hosting** section → Click **Edit**.
* Select **Enable** → Index document: Enter `index.html`. Click **Save changes**.
![Activate Static Hosting](/fcj-workshop-template/images/5-Workshop/5.6-Frontend-S3/s3-static-hosting.png)


**Acceptance results:** When accessing the CloudFront (or S3 Endpoint) URL, your WeDo Workspace interface will appear extremely smooth, and all functions connected to the Backend will operate perfectly!
![Website operation results](/fcj-workshop-template/images/5-Workshop/5.6-Frontend-S3/s3-result.jpg)