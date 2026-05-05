# SERVERLESS STATIC WEBSITE DEPLOYMENT ON AWS USING S3, CLOUDFRONT & ROUTE 53
This project demonstrates how to host a static website using AWS S3, CloudFront, and Route 53.
AWS S3 (Simple Storage Service) is a cloud storage service used to store and retrieve files (called objects) over the internet. It is a highly scalable and durable service which stores data in buckets and is commonly used for backups, images, videos and website files.
A Static Website is one made of fixed files (HTML, CSS, JavaScript) that do not change based on user input. It provides same content for every user, no database or backend server and could be used for portfolio and landing page. 
Launching a static website requires creating an s3 bucket on AWS and applying appropriate policy then create a simple website files and store on your computer.

## Step 1: Create an S3 Bucket and website file 
- Create a simple website file (Example index.html) and store on your computer, then search for S3 service and create an S3 bucket, name it "project-alpha-s3" (bucket name must be globally unique).
<img width="1827" height="688" alt="Bucket name" src="https://github.com/user-attachments/assets/f21c74fa-c833-44ca-9d08-ed5bd241400a" />

- Uncheck block all public access (required for hosting and accessing a static website using bucket endpoint URL). Then click on create bucket. 
<img width="1833" height="552" alt="blocking public access" src="https://github.com/user-attachments/assets/86be87d4-5b38-4c1a-b609-bfe0dba3558e" />


## Step 2: Uploading files 
Open your bucket, click upload and search for your website file. Add the index.html file and other files if needed then click upload
<img width="1856" height="670" alt="adding index html file" src="https://github.com/user-attachments/assets/e34b05e7-6858-4ab0-9515-adcd2ca0ed26" />

## Step 3: Enable Static Website Hosting
Navigate through the properties tab of your bucket and Check Enable static website hosting. Set the index.html document and save.
<img width="1840" height="666" alt="enable static website hosting" src="https://github.com/user-attachments/assets/6516d15a-faee-4e2d-99ea-8a69618fceca" />

## Step 4: Set Bucket Policy and access Your Website
- Configure bucket policy to grant read permission making Files Public.
<img width="1858" height="706" alt="bucket policy" src="https://github.com/user-attachments/assets/19de42c9-3273-40ad-a643-0e7c24a12765" />

- Go back to properties and scroll to static website hosting and copy your bucket Endpoint URL
<img width="1831" height="523" alt="static website URL" src="https://github.com/user-attachments/assets/87813c75-d4d9-4117-86c1-7ab3f96b3a07" />

- Copy your bucket Endpoint URL and paste in your browser.
<img width="1927" height="968" alt="Display web page" src="https://github.com/user-attachments/assets/c9a4bd2b-9c1c-42d2-81de-1047507ca97e" />

## Step 5: CloudFront distribution
- Created a cloudFront distribution allowing web application firewall (WAF) as first line security
<img width="1836" height="675" alt="create cloudfront" src="https://github.com/user-attachments/assets/0d0d6eb6-5ccb-407b-8e81-1c08992baba9" />

- Set the distribution origin to the S3 bucket (project-alpha-s3).
<img width="1843" height="696" alt="CF-origin" src="https://github.com/user-attachments/assets/2cd8e6ca-5fec-4a54-81c9-20e11812c313" />

- Enabled default root object to index.html file
<img width="1807" height="687" alt="setting rout objet" src="https://github.com/user-attachments/assets/106c9199-ab92-4f46-a0fb-74d434729508" />



## Step 6: Secure S3 (important change)
- Restrict public access to bucket by block direct public access to the S3 bucket
<img width="1852" height="624" alt="block bucket public access" src="https://github.com/user-attachments/assets/26817872-6531-48bd-a729-66695fdabead" />

- Verify an updated bucket policy to grant S3 access only through CloudFront.
<img width="1372" height="735" alt="New bucket policy" src="https://github.com/user-attachments/assets/4f4e3d50-348c-4df5-958e-72499fad9270" />

- Created and use origin access control (OAC) to allow bucket content access only with cloudfront.
<img width="784" height="730" alt="origin access control" src="https://github.com/user-attachments/assets/d3bc8555-e7b2-47dc-a09c-4c0aef14f58e" />

- Use of cloudfront ditribution domain name to access the static webpage
<img width="1891" height="852" alt="CF-web page view" src="https://github.com/user-attachments/assets/3d6f647e-69f2-4109-8628-09aae3eacbfd" />

## Step 7: Route 53 DNS
- Created a hosted zone and registered a domain name using rouute 53 "brandi.click"
<img width="1362" height="742" alt="creating a hosted zone" src="https://github.com/user-attachments/assets/d8e23b1f-1a4d-44fa-a1dd-1d0bb4cef6a5" />

- Created an A (Alias) record to routing traffic
<img width="1488" height="648" alt="create A-record" src="https://github.com/user-attachments/assets/4934bcb5-e32c-413f-b601-62524f6cc893" />

- Set cloudFront distribution as the endpoint of A record to, route traffic to cloudfront
<img width="1813" height="706" alt="route traffic to route 53" src="https://github.com/user-attachments/assets/01cfdee8-94d0-45eb-829d-2aceb7382670" />

- Add the domain name "brandi.click" to cloudFront as an alternate domain name  
<img width="1851" height="690" alt="alternate domain name" src="https://github.com/user-attachments/assets/1bd9bec3-6e98-4688-bf62-a58c65a6bfe5" />

- Request wildcard certificate from AWS Certificate Manager for flexibility and ability to ability to host multiple domains, contrary to SSL/TLS certificate. 
<img width="1849" height="676" alt="creating certificate" src="https://github.com/user-attachments/assets/29f4918b-87cd-40ce-83bb-4e809ba58212" />

- Add certificate and domain name to the cloudFront distribution
<img width="1876" height="598" alt="add certificate and domain name" src="https://github.com/user-attachments/assets/dae75055-b3c6-4103-aa09-c139302d1414" />
 
## Use domain name to access website hosted on S3 through cloudFront distribution and cache sites
<img width="950" height="446" alt="image" src="https://github.com/user-attachments/assets/6e1185df-f561-487d-bf25-015b49bec1d8" />

