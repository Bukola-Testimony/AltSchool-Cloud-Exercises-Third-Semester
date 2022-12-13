# AltSchool-Cloud-Exercises-Third-Semester
> ![AltSchool Cloud Exercices](/cloud3.JPG)


- [Back to first page](../README.md)
- [Overview](#overview) 
- [Task](#TASKS) 
- [Process](#Process)
- [Getting started](#Getting-Started)
- [Author](#author)

<br>
<br>

## Overview
### LEARNING CLOUD ENGINEERING WITH ALTSCHOOL.
> This is actually about the third week in third semester with AltSchool.There has been so much new concepts to learn. Introduction to Cloud providers starting with AWS and its services was an incredibly enriching experience. With the guidance of instructors both physical and on LMS, I was able to dive deep into the world of AWS and gain a comprehensive understanding of its different services. Through hands-on labs, tutorials, and interactive quizzes, I was able to learn best practices for architecting and managing applications on AWS as well as effective methods for managing costs and and the various ways of deploying applications on the cloud. This week the focus is on s3 bucket

<br>



## **TASKS**

- Create an S3 bucket, with a time stamp and your name
- Enable static website hosting, and bucket must be private
- The tutor must be able to access your URL.
- Explore Cloudfront, to privately expose your index.html file in your S3 bucket.

<br>

## Process

- Log in to your AWS account and navigate to the S3 service.
- Click on the "Create bucket" button.
- Enter a unique bucket name for the source bucket and select a region.
- Click on the "Create" button to create the source bucket.
- Repeat the previous steps to create a second bucket for the destination of the cross-origin replication.
- In the source bucket properties, click on the "Cross-Origin Replication" option.
- Select the destination bucket and click on the "Add" button to add it as a replication destination.
- In the "Replication Rules" section, create a new replication rule to specify the files and folders that you want to replicate from the source bucket to the destination bucket.
- Enable the replication rule and click on the "Save" button to apply the changes.
- Test the replication by uploading a file to the source bucket and verifying that it appears in the destination bucket.
- Monitor the replication process using the S3 metrics and logs to ensure that the files are being replicated successfully.

<br>

## Getting Started

## 1. Create an s3 Bucket

Navigate to the S3 dashboard, and click on the Create bucket button. It will launch a new wizard

![s1](/Exercise-1/images/s1.png)

We create a bucket first, and later we upload files and folders to it.

## 2. General configuration

Provide the bucket-name. The bucket name must be unique worldwide e.g. demo-bucket-2022-12-09, and must not contain spaces or uppercase letters.

![s1](/Exercise-1/images/s2.png)

## 3. Private Access settings

Bock all public access.

![s1](/Exercise-1/images/s3.png)

## 4. Bucket Versioning and Encryption

- Bucket Versioning - You may leave it disable. Note: if you want to set up bucket replication or static website you have to enable versioning


<br>
<br>

## Author

- Website - [Bukola Testimony](https://bukola-testimony.github.io/My-Portfolio-website/)
- Twitter - [@BukolaTestimony](https://twitter.com/BukolaTestimony)
