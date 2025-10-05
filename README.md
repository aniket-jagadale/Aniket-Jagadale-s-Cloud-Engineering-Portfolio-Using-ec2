# Static Website Hosting on AWS S3 (Personal Resume)

This project demonstrates how to host a static website using **Amazon S3 bucket**. The website serves as a professional portfolio for a **Cloud Engineering Specialist**.

![](/img/Screenshot%20(227).png)
---

## 📘 Project Overview

This static website hosts a professional resume/portfolio page that showcases cloud engineering skills and expertise. The website is deployed on **AWS S3** with proper bucket policies for public access.

---

## ✨ Features

- Responsive static HTML webpage  
- Professional portfolio layout  
- Cloud engineering focus section  
- Skills and contact information  
- AWS S3 bucket configuration for web hosting  

---

## ⚙️ AWS S3 Configuration

### 🪣 Bucket Policy

The bucket is configured with a policy that allows public read access to objects:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Statement1",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::your-bucket-name/*"
    }
  ]
}
```

### 📦 S3 Bucket Properties

- **Region:** Asia Pacific (Mumbai) `ap-south-1`  
- **Static Website Hosting:** Enabled  
- **Index Document:** `index.html`  
- **Storage Class:** Standard  

---

## 🖼️ Screenshots

The following screenshots demonstrate the S3 configuration:

1. **Main Webpage Content** — `Screenshot-227.png`  
2. **S3 Object Overview** — `Screenshot-228.png`  
3. **Bucket Policy Configuration** — `Screenshot-229.png`  

---

## 🚀 Deployment Steps

### 1️⃣ Create S3 Bucket
- Create a new S3 bucket with a unique name  
- Enable static website hosting in bucket properties  

### 2️⃣ Upload Files
- Upload `index.html` and any assets to the bucket  
- Set appropriate permissions for public read access  

### 3️⃣ Configure Bucket Policy
- Apply the bucket policy shown above to allow public access  

### 4️⃣ Access Website
- Use the S3 website endpoint URL to access your static website  

## 📂 File Structure

```
s3-bucket/
├── index.html          # Main webpage file
```

---

## 🧰 Technologies Used

- **AWS S3:** For static website hosting  
- **HTML:** For webpage structure  
- **CSS:** For styling (embedded in HTML)  
- **AWS IAM:** For bucket policies and permissions  

---

## ⚠️ Important Notes

- Ensure the bucket policy is properly configured for public access  
- The bucket name must be unique across all AWS S3 buckets  
- Enable static website hosting in the S3 bucket properties  
- Upload all required files with public read permissions  

---

## 🔒 Security Considerations

- Only enable public read access for static content  
- Regularly review and update bucket policies  
- Monitor S3 access logs for unusual activity  
- Use **CloudFront** for additional security and performance  

---

## 📄 License

This project is for **demonstration purposes** of AWS S3 static website hosting capabilities.
