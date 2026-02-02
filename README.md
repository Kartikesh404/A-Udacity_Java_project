
# Deploy Static Website on AWS

## Project Overview

This project demonstrates how to deploy a **static website** using **Amazon Web Services (AWS)**. The website consists only of **HTML, CSS, and JavaScript files**, requiring no server-side processing.

The project focuses on:

* Hosting static files in **Amazon S3**
* Distributing content globally using **Amazon CloudFront (CDN)**
* Applying security best practices for public content delivery

---

## Architecture Overview

The architecture follows a secure and scalable cloud design:

* **Amazon S3** stores the static website files.
* **Amazon CloudFront** acts as a Content Delivery Network (CDN) to:

  * Reduce latency
  * Improve loading speed
  * Secure access to S3 content

In this project, CloudFront is configured to access the S3 bucket securely rather than exposing the bucket publicly.

---

## Steps Performed

### 1. Create an S3 Bucket

* Created an S3 bucket with a **globally unique name**
* Disabled public access to follow security best practices
* Uploaded all website files (`index.html`, CSS, JS, assets)

### 2. Configure Bucket Permissions

* The bucket itself remains **private**
* Access is controlled using CloudFront (recommended approach)
* This avoids exposing S3 objects directly to the public

### 3. Create CloudFront Distribution

* Selected the S3 bucket as the **origin**
* Configured **Origin Access Control (OAC)** to allow CloudFront to securely fetch objects
* Enabled:

  * HTTP to HTTPS redirection
  * Default caching behavior

### 4. Access the Website

* The website is accessed using the **CloudFront distribution domain name**
* CloudFront caches content at edge locations for faster delivery

---

## Security Considerations

* The S3 bucket is **not publicly accessible**
* Only CloudFront is allowed to read objects from the bucket
* This approach is more secure than traditional S3 static website hosting

---

## CloudFront Permission Note (Udacity Lab Environment)

While creating the CloudFront distribution, the following permission error may appear in the Udacity AWS lab:

> `pricingplanmanager:CreateSubscription is not authorized`

This issue occurs due to **restricted IAM permissions in the student sandbox environment** and is a known limitation.
It is **not caused by incorrect configuration**.

All required steps for CloudFront setup were followed according to AWS best practices.

---

## Files Included

```
.
├── index.html
├── css/
│   └── styles.css
├── js/
│   └── script.js
├── assets/
│   └── images/
└── README.md
```

---

## Technologies Used

* Amazon S3
* Amazon CloudFront
* HTML
* CSS
* JavaScript

---

## Outcome

* Static website successfully hosted on AWS
* Content delivered efficiently using CloudFront CDN
* Secure and scalable cloud architecture implemented

