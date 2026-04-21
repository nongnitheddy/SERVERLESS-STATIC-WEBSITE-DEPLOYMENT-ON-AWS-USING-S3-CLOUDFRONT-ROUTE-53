# SERVERLESS STATIC WEBSITE DEPLOYMENT ON AWS USING S3, CLOUDFRONT & ROUTE 53
AWS S3 (Simple Storage Service) is a cloud storage service used to store and retrieve files (called objects) over the internet. It is a highly scalable and durable service which stores data in buckets and is commonly used for backups, images, videos and website files.
A Static Website is one made of fixed files (HTML, CSS, JavaScript) that do not change based on user input. It provides same content for every user, no database or backend server and could be used for portfolio and landing page. 
Launching a static website requires creating an s3 bucket on AWS and applying appropriate policy then create a simple website files and store on your computer.
## Step 1: Create an S3 Bucket and website file 
Create a simple website file (Example index.html) and store on your computer, then search for S3 service and click create AWS s3 bucket. The bucket name must be globally unique (example project-alpha-s3) and uncheck block all public access (this is required for hosting a static website). Then click on create bucket.  
## Step 2: Uploading files 
Open your bucket, click upload and search for your website file and add the index.html file. (and other files if needed then click upload
## Step 3: Enable Static Website Hosting
Open your bucket and navigate to the properties tab. Scroll down the properties tab to static website hosting check Enable static website hosting. Set the index.html document and save.
## Step 4: Set Bucket Policy and access Your Website
Go to permissions, scroll down to bucket policy and configure the permission making Files Public. Go back to properties and scroll to static website hosting. Copy your bucket Endpoint URL and paste it in your browser.
## Step 5: Enable CloudFront
Go to Amazon CloudFront and create a CloudFront distribution. The origin was set to my S3 bucket. Enable default root object to index.html.
## Step 6: Secure S3 (important change)
Do NOT use public S3 website hosting anymore. Blocks direct public access to S3. CloudFront will access S3 securely using an Origin Access Control (OAC). This blocks direct public access to S3. 
## Step 7: Add HTTPS (SSL security)
Request a free certificate by navigating to AWS Certificate Manager. Then the domain name was added (example: www.yoursite.com) and validated through the DNS 
Step 5: Connect custom domain
Go to Amazon Route 53 and create hosted zone for your domain. Add record; Type: A (Alias) and points to CloudFront distribution 👉 www.yoursite.com → CloudFront. 
## Testing your website
Test your website (https://www.yoursite.com). You should see your S3 website loading securely. 
