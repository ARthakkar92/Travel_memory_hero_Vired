# Travel_memory_hero_Vired
# The TravelMemory application is a MERN stack application deployed on AWS infrastructure using:  
Amazon EC2  
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
# Backend Deployment Steps
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

# Backend Load Balancer
Target group port: 80
Health check path: /

<img width="1869" height="886" alt="image" src="https://github.com/user-attachments/assets/76980f28-3321-41c2-8f2c-e196435f4e7c" />





