# SERVERLESS STATIC WEBSITE DEPLOYMENT ON AWS USING S3, CLOUDFRONT & ROUTE 53
AWS S3 (Simple Storage Service) is a cloud storage service used to store and retrieve files (called objects) over the internet. It is a highly scalable and durable service which stores data in buckets and is commonly used for backups, images, videos and website files.
A Static Website is one made of fixed files (HTML, CSS, JavaScript) that do not change based on user input. It provides same content for every user, no database or backend server and could be used for portfolio and landing page. 
Launching a static website requires creating an s3 bucket on AWS and applying appropriate policy then create a simple website files and store on your computer.
## Step 1: Create an S3 Bucket and website file 
Create a simple website file (Example index.html) and store on your computer, then search for S3 service and create an S3 bucket, name it "project-alpha-s3" (bucket name must be globally unique). Uncheck block all public access (required for hosting and accessing a static website using bucket endpoint URL). Then click on create bucket.  
## Step 2: Uploading files 
Open your bucket, click upload and search for your website file. Add the index.html file and other files if needed then click upload
## Step 3: Enable Static Website Hosting
Navigate through the properties tab of your bucket and Check Enable static website hosting. Set the index.html document and save.
## Step 4: Set Bucket Policy and access Your Website
Configure bucket policy to grant read permission making Files Public. Go back to properties and scroll to static website hosting and copy your bucket Endpoint URL and paste in your browser.
## Step 5: CloudFront distribution
- Created a cloudFront distribution and set the origin to the S3 bucket (project-alpha-s3).
- Enabled default root object to index.html file
- Created and use origin access control (OAC) to allow bucket content access only with cloudfront.
## Step 6: Secure S3 (important change)
- Blocked direct public access to S3
- Updated bucket policy to grant S3 access only through CloudFront. This blocks public access to S3.
- Enabled web application firewall (WAF) as first line security
- Use of cloudfront ditribution domain name to access the static webpage
## Step 7: Route 53 DNS
- Created a hosted zone and registered a domain name using rouute 53 "brandi.click"
- Created an A (Alias) record, routing traffic to cloudFront distribution
- Use the domain name "brandi.click" to access the S3 static website 
## Step 8: Add HTTPS (SSL security)
- Request  milcraft certificate from AWS Certificate Manager. 
- Add the certificate and domain name to cloudFront as alternate domain name  
## Use route 53 domain name to access website hosted on S3 through cloudFront distribution and cache sites
