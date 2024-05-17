# Deployment-of-a-Static-Website-Using-AWS-S3-and-CloudFront
This project outlines the steps to set up a static website using AWS services. We'll use S3 to host website files, set a public read policy on a private bucket, and deliver content globally via CloudFront. This guide is aimed at demonstrating a straightforward method for secure and efficient website deployment on AWS.
---

But, you might be wondering what is CloudFront and what is its usefullness. According to Amazon Web Service Amazon CloudFront speeds up distribution of your static and dynamic web content, such as .html, .css, .php, image, and media files. When users request your content, CloudFront delivers it through a worldwide network of edge locations that provide low latency and high performance.
---
---
# Creating and Configuring the S3 Bucket

After logging into my AWS account, I headed straight to the S3 service by searching for "S3" in the console's search bar. I needed to create a new bucket for my static website, so I clicked on "Create bucket." I named this bucket  
   "cloud-web-app123"

![picture](./images/CL-1.png)

![picture](./images/CL-2.png)

![picture](./images/CL-3.png)


2- Once the bucket was set up, I clicked on its name to access it. Here, I found the option to upload files. I clicked on "Upload" and selected the static files for my website—HTML, CSS, and any images I planned to use. After confirming all files were ready, I clicked "Upload" to move everything to the root directory of my new S3 bucket.

![picture](./images/CL-5.png)


*  Uploaded folders


![picture](./images/CL-6.png)


* Uploaded files


![picture](./images/CL-7.png)

3.Once my files were uploaded, the next step was to make them accessible as a website. To do this, I navigated to the Permissions tab of my bucket. Here, I found the option for Static website hosting. I clicked on it to configure the settings needed to serve my static content. I enabled static website hosting by selecting the option "Use this bucket to host a website." In the text boxes provided, I entered the name of my index document which is **index.html**. After filling in these details, I saved the settings.


![picture](./images/CL-8.png)


![picture](./images/CL-9.png)


![picture](./images/CL-10.png)


4. Next, i went to the bucket, i selected the objects then actions, Make public using ACL.
After that i went to the properties of my bucket, copied the URL of the static website, opened a new tab and pasted it. My webapp is accessible but NOT SECURE. In this case, we need to configure a CloudFront Distribution to make it secure.

![picture](./images/CL-11.png)


![picture](./images/CL-12.png)


![picture](./images/CL-13.png)


![picture](./images/CL-14.png)
---
---
#   Setting Up AWS CloudFront
5- After configuring my S3 bucket to host the static website, I moved on to setting up AWS CloudFront to distribute the content globally. First, I navigated to the CloudFront service by searching for "CloudFront" in the AWS Management Console.

6- I initiated the creation of a new distribution by clicking on Create distribution. For the origin domain, I selected my S3 bucket URL from the dropdown, In setting up the origin access, I chose the Origin access control settings. I clicked on Create new OAC, and a pop-up appeared where I verified that my origin name was correctly showing. I left all other settings default and proceeded to create the OAC. Also i went to the my bucket permission and Block all public access.

![picture](./images/CL-15.png)

![picture](./images/CL-16.png)

![picture](./images/CL-17.png)

![picture](./images/CL-18.png)

![picture](./images/CL-19.png)

![picture](./images/CL-20.png)

7- Continuing with the configuration, I scrolled down to the distribution settings and set the Default root object to **index.html**, ensuring that CloudFront serves the **index.html** file when accessing the root URL of the distribution.

![picture](./images/CL-21.png)

8-  Upon clicking Create distribution, CloudFront began to deploy, and it automatically generated a new policy for the S3 bucket. I copied this policy and went back to my S3 bucket settings to update the policy accordingly. This ensures that the permissions are correctly set to allow CloudFront to access the S3 bucket.

![picture](./images/CL-22.png)

![picture](./images/CL-23.png)

9- Went the CloudFront Distribution was Enable, i clicked on the distribution ID, copied the distribution domain name and pasted in a new tab  my browser.

Behold, my static-website was successfully deployed and secure as expected.

![picture](./images/CL-24.png)

![picture](./images/CL-25.png)

So, this is how to host a static website on a s3 bucket and be able to access it using CloudFront.
