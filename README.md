# Travel_memory_hero_Vired
# The TravelMemory application is a MERN stack application deployed on AWS infrastructure using:  
Amazon EC2  
Amazon Machine Images (AMI)
Application Load Balancer (ALB)  
Nginx Reverse Proxy  
MongoDB Atlas  
Cloudflare DNS  
AWS Certificate Manager (ACM)  
The deployment ensures:  
High availability  
Load balancing  
Secure HTTPS communication  
Scalable architecture
#  Infrastructure Architecture
Components Used
2 Frontend EC2 Instances
2 Backend EC2 Instances
1 Backend Load Balancer
1 Frontend Load Balancer
MongoDB Atlas (Cloud Database)
Cloudflare (DNS & SSL)
ACM (SSL Certificate)

# Clone Repository
## Backend Deployment Steps
1) git clone https://github.com/UnpredictablePrashant/TravelMemory.git
cd backend
<img width="620" height="214" alt="image" src="https://github.com/user-attachments/assets/b1b9a3b7-3d14-4957-9411-8497a52f2c51" />

2) Install Dependencies
npm install

3) Create .env file:
PORT=3001
MONGO_URI=<MongoDB Atlas Connection String>
<img width="861" height="85" alt="image" src="https://github.com/user-attachments/assets/2fd3ae10-1c2b-43c7-8152-7a9dc1762ebc" />

4) Start Backend Application
   node index.js
   http://localhost:3001

5) Configure Nginx Reverse Proxy
/etc/nginx/nginx.conf

server {
    listen 80;

    location / {
        proxy_pass http://localhost:3001;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}       location / {
    proxy_pass http://localhost:3001;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
}

<img width="1386" height="178" alt="image" src="https://github.com/user-attachments/assets/85368480-732a-47ad-897c-87427f68d83c" />

## Backend AMI image.
After configuring the initial backend EC2 instances, Amazon Machine Images (AMI) were created to replicate the configured environment.

<img width="1874" height="885" alt="image" src="https://github.com/user-attachments/assets/190d80d9-2b81-4141-be04-de0104deee99" />


## Backend Load Balancer Target Group
Target group port: 80

Health check path: /hello

<img width="1917" height="856" alt="image" src="https://github.com/user-attachments/assets/4ff4b845-3c44-40ac-8bd0-64acb1d8f781" />

<img width="1655" height="742" alt="image" src="https://github.com/user-attachments/assets/92fb6103-24c7-4d67-8cdd-b5dd126554bb" />

# Frontend Deployment Steps
## Clone Repository
cd frontend
npm install

## Configure Backend URL
updated src/url.js
export const baseUrl = "/api";

## Build React App
npm run build

## Configure Nginx

<img width="1033" height="355" alt="image" src="https://github.com/user-attachments/assets/833f5329-b4a3-4665-b6bc-14a2ec6bc599" />

## Frontend AMI image.
After configuring the initial frontend EC2 instances, Amazon Machine Images (AMI) were created to replicate the configured environment.

<img width="1879" height="857" alt="image" src="https://github.com/user-attachments/assets/07231b8e-0ea7-41da-88cf-f0d0af8ced58" />


## Frontend Load Balancer Target Group

Target group port: 80

Health check path: /

<img width="1661" height="769" alt="image" src="https://github.com/user-attachments/assets/e3d56e4f-d058-4f68-894e-7577b6c64bcb" />

<img width="1645" height="397" alt="image" src="https://github.com/user-attachments/assets/267ce9eb-dc77-49f8-873b-c3f7a297343f" />

# Domain Configuration with Cloudflare

## Add Domain
akplacesolution.com

## DNS Records

<img width="1874" height="336" alt="image" src="https://github.com/user-attachments/assets/65c8b9a0-2875-4330-af24-84c3e8c04d85" />

## SSL Setup

<img width="1875" height="364" alt="image" src="https://github.com/user-attachments/assets/18ded0ac-4d1d-4619-bc3a-2506a9a6050a" />

<img width="1844" height="614" alt="image" src="https://github.com/user-attachments/assets/9878bc64-69b0-4779-9e49-44ed3d390fb7" />

# Load Balancing and Scaling

Multiple EC2 instances were added to target groups to ensure:

High availability

Fault tolerance

Efficient traffic distribution

Verification done by:

Checking target group health

Refreshing page and verifying traffic distribution

<img width="1677" height="785" alt="image" src="https://github.com/user-attachments/assets/940b1f3d-fe0d-4db1-9b92-e42e74ed1bcc" />

# Application URL
Application accessible securely over HTTPS.

<img width="1891" height="949" alt="image" src="https://github.com/user-attachments/assets/a424c1cf-d9c1-409a-bbc0-155340460bd4" />












