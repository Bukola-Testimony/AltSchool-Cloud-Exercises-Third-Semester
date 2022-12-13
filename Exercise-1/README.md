# AltSchool-Cloud-Exercises-Third-Semester
> ![AltSchool Cloud Exercices](/cloud3.JPG)


- [Back to first page](../README.md)
- [Overview](#overview) 
- [Task](#TASKS) 
- [Process](#Process)
- [Author](#author)

<br>
<br>

## Overview
LEARNING CLOUD ENGINEERING WITH ALTSCHOOL.
<p>
This is actually about the third week in third semester with AltSchool.There has been so much new concepts to learn. Introduction to Cloud providers starting with AWS and its services was an incredibly enriching experience. With the guidance of instructors both physical and on LMS, I was able to dive deep into the world of AWS and gain a comprehensive understanding of its different services. Through hands-on labs, tutorials, and interactive quizzes, I was able to learn best practices for architecting and managing applications on AWS as well as effective methods for managing costs and and the various ways of deploying applications on the cloud. This week the focus is on s3 bucket
</p>




## **TASKS**

- Create an S3 bucket, with a time stamp and your name

- Enable static website hosting, and bucket must be private

- The tutor must be able to access your URL.

- Explore Cloudfront, to privately expose your index.html file in your S3 bucket.

## Process

- Log in to your AWS account and navigate to the S3 service.

- Click on the "Create bucket" button.

- Enter a unique bucket name that includes a time stamp and your name. For example, "johnsmith-2021-04-23-12".

- Select a region for your bucket and click on "Create".

- In the bucket properties, click on the "Static website hosting" option.

- Enable static website hosting and enter the name of the index file for your website. For example, "index.html".

- Click on "Save" to apply the changes.

- In the bucket permissions, make sure the bucket and its content are set to private by selecting the "Block all public access" option.

- Click on the "Save" button to apply the changes.

- Navigate to the Cloudfront service in your AWS account and click on the "Create Distribution" button.

- In the Origin settings, select the S3 bucket you created in the previous steps as the origin domain name.

- In the "Origin access" settings, select "Legacy access identities" (This will Use a CloudFront origin access identity (OAI) to access the S3 bucket)

- From the dropdown, under "Origin access identity" settings, click on "Create new OAI" Here, your s3 bucket name is automatically generated in the box. Click on "create"

-  Next, under bucket policy, select "Yes, update the bucket policy"

- In the Default Cache Behavior settings under "Viewer settings, select the "Redirect HTTP to HTTPS" option.

- Scroll down to "Settings" and  under the "Default root object" type in the root document for web in s3 bucket e.g index.html

- Scroll to the end and click on the "Create Distribution" button.

- Wait for the Cloudfront distribution to be created and enabled.

- Test the Cloudfront URL to make sure the index.html file in your S3 bucket is privately exposed and only accessible from the Cloudfront URL.



## Getting Started

## Prerequisite

- Amazon Account
- An **index.html** file on local machine

## 1. Create a Bucket

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

- Encryption - If enabled, it will encrypt the files being stored in the bucket.

- Object Lock - If enables, it will prevent the files in the bucket from being deleted or modified

![s1](/Exercise-1/images/s4.png)

## 5. Upload File/Folders to the Bucket

From the S3 dashboard, click on the name of the bucket you have created in the step above

![s1](/Exercise-1/images/s5b.png)

The snapshot above shows that the bucket is in the Region: US East (N. Virginia) us-east-1, and it has a unique Amazon resource name (ARN): arn:aws:s3:::my-demo-bucket-2022-10/index.html. You can view more details of the bucket.

In the snapshots above, we have created a private bucket. Let's see how to upload files and
folders to the bucket, and configure additional settings.

Click on the Upload button to upload files and folders into the current bucket. In the snapshot below, I have uploaded a index.html file.

![s1](/Exercise-1/images/s8.png)

![s1](/Exercise-1/images/s6.png)

![s1](/Exercise-1/images/s10.png)

## 6. Enable Static Website Hosting

Click on your bucket properties

![s1](/Exercise-1/images/s11.png)

Scroll down to the bottom page and click on Edit icon

![s1](/Exercise-1/images/s12.png)

In the index document, write the name of your uploaded html file and click on **save changes**

![s1](/Exercise-1/images/s13.png)

![s1](/Exercise-1/images/s14.png)

## 7. **Create Distribution**

![s1](/Exercise-1/images/n1.png)

Now we will create CloudFront Distribution for our bucket. Currently, we do not have any distributions. We will click on Create Distribution.

![s1](/Exercise-1/images/c1.png)

Here we will provide the Origin domain which in our case is from Amazon S3 i.e. **my-demo-bucket-2022-10.s3.us-east-1.amazonaws.com**. Note that an origin is a location where content is stored, and from which CloudFront gets content to serve to viewers.

![s1](/Exercise-1/images/c2.png)

In S3 bucket access, we will select Yes use OAI as we are only restricting user access to CloudFront. To restrict access to content that we serve from Amazon S3 buckets, these steps are followed.

Creation of a special CloudFront user called an origin access identity (OAI) and its association with our distribution.
Configuration of S3 bucket permissions so that CloudFront can use the OAI to access the files in our bucket and serve them to our users. Make sure that users can’t use a direct URL to the S3 bucket to access a file there.

In Origin access identity, we will click on Create new OAI. For Bucket policy, we will select Yes, update the bucket policy. Here we are updating the bucket policy to allow read access to the OAI.

![s1](/Exercise-1/images/c3.png)

Here we will get a default name for OAI then we will click on Create.

![s1](/Exercise-1/images/c4.png)

After these steps are taken, users can only access our files through CloudFront, not directly from the S3 bucket.

Redirect all HTTP request to HTTPS

![s1](/Exercise-1/images/c5.png)

In the **Default root object**, we will write the name of the file i.e. index.html that we uploaded to our bucket.
![s1](/Exercise-1/images/c6.png)

Now after creating our distribution we can view our newly created OAI.

![s1](/Exercise-1/images/c8.png)

**Note** Remember, as soon as your CloudFront distribution is Deployed, it attaches to S3 and starts caching the S3 private pages. Once the caching is complete, the CloudFront domain name URL will stop redirecting to the S3 object URL. CloudFront may take 10-30 minutes (or more) to cache the S3 page, and you will be able to view the webpage, as shown below.

Now to check whether things are working properly let's test our CloudFront Distribution. We will copy the Distribution domain name and enter it into our browser.

![s1](/Exercise-1/images/c9.png)

Our CloudFront Distribution is working perfectly fine. We have successfully learned that how to use CloudFront with S3.

![s1](/Exercise-1/images/rendered-page.png)


<br>
<br>

## Author

- Website - [Bukola Testimony](https://bukola-testimony.github.io/My-Portfolio-website/)
- Twitter - [@BukolaTestimony](https://twitter.com/BukolaTestimony)
