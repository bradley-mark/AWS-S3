# Configuring a static website on Amazon S3

**Simple overview**

![image](https://user-images.githubusercontent.com/91480603/211607509-8806d29f-396a-418a-bf00-337ed41e6c09.png)

Amazon Simple Storage Service (Amazon S3) can host static websites without a need for a web server. 

In this solution, there are no Windows or Linux servers to manage, and no need to provision machines, install operating systems, or fine-tune web server configurations. There’s also no need to manage storage infrastructure (such as, SAN, NAS) because Amazon S3 provides practically limitless cloud-based storage. Fewer moving parts means fewer troubleshooting headaches.

# Scalability and availability

Amazon S3 is inherently scalable. For popular websites, Amazon S3 scales seamlessly to serve thousands of HTTP or HTTPS requests per second without any changes to the architecture.

In addition, by hosting with Amazon S3, the website is inherently highly available. Amazon S3 is designed for 99.999999999% durability, and carries a service level agreement (SLA) of 99.9% availability.

# Setup

# Create a bucket

1. Sign in to the AWS Management Console and open the Amazon S3 console at **https://console.aws.amazon.com/s3/**
2. Choose **Create bucket**
3. Enter the **Bucket name** (e.g. s3.markbradley.cloud)
4. Choose the Region (US East (N.Virginia) us-east-1)
5. To accept the default settings and create the bucket, choose **Create**

# Enable static website hosting

1. Select **bucket**
2. Choose **Properties**
3. Under **Static website hosting**, choose **Edit**
4. Choose **Static website hosting**, choose **Enable**
5. In **Index document**, enter the file name of the index document, typically index.html
6. In **Error document**, enter the custom error document file name, typically error.html
7. Choose **Save changes**
8. Under **Static website hosting**, note the **Endpoint**

![image](https://user-images.githubusercontent.com/91480603/211651115-32bf92a7-5225-463e-a962-83e9e3647623.png)

# Edit Block Public Access settings
By default, Amazon S3 blocks public access to your account and buckets.

1. Choose **Permissions**
2. Under **Block public access (bucket settings)**, choose **Edit**
3. Clear **Block all public access**, and choose **Save changes**
4. Confirm the settings

# Add a bucket policy that makes your bucket content publicly available

1. Choose **Permissions**
2. Under **Bucket Policy**, choose **Edit**
3. To grant public read access for your website, copy the following bucket policy, and paste it in the **Bucket policy editor**

![image](https://user-images.githubusercontent.com/91480603/211653440-9ca96179-b81d-4fbb-a1ef-f36f331b3d2a.png)

4. Choose **Save changes**

# Configure an index document

1. Create an index.html file
2. Select **bucket**
3. Choose **Objects**
4. Choose **Upload**
5. **Add files** - index.html
6. Choose **Upload**

# Configure an error document

1. Create an error.html file
2. Select **bucket**
3. Choose **Objects**
4. Choose **Upload**
5. **Add files** - error.html
6. Choose **Upload**

![image](https://user-images.githubusercontent.com/91480603/211665290-e656fd18-57aa-4d69-a7a1-c5dce1d1d03b.png)

# Test your website endpoint

1. Select **bucket**
2. Choose **Properties**
3. View bottom of page - **Static website hosting** - **Bucket website endpoint**

**http://s3.markbradley.cloud.s3-website-us-east-1.amazonaws.com**

![image](https://user-images.githubusercontent.com/91480603/211665812-ebc7df1a-91a7-4943-80ee-bdc9fee82473.png)

**Note:** Amazon S3 does not support HTTPS access to the website. If you want to use HTTPS, you can use Amazon CloudFront to serve a static website hosted on Amazon S3.
