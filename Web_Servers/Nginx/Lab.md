# 🔹 Hands-On Lab: Nginx Reverse Proxy for a Dynamic Node.js Application

# 🎯 Objective

Deploy a dynamic Node.js application behind Nginx using Docker Compose.

# 🏗️ Architecture

Browser → Nginx (Port 80) → Node.js App (Port 3000)

## 🔹 Step 1: Create Project Structure
```
mkdir nginx-node-lab

cd nginx-node-lab

mkdir app nginx
```
## 🔹 Step 2: Create a Simple Node.js Application

### 📄 app/server.js
```
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello from the Dynamic Node.js Application!');
});

app.get('/api', (req, res) => {
  res.json({ message: 'This is a dynamic API response' });
});

app.listen(3000, () => {
  console.log('Server running on port 3000');
});
```

### 📄 app/package.json
```
{
  "name": "node-app",
  "version": "1.0.0",
  "description": "Simple Node.js app",
  "main": "server.js",
  "dependencies": {
    "express": "^4.18.2"
  }
}
```
## 🔹 Step 3: Create the Node.js Dockerfile

### 📄 app/Dockerfile
```
FROM node:18-alpine
WORKDIR /usr/src/app
COPY package.json .
RUN npm install
COPY . .
EXPOSE 3000
CMD ["node", "server.js"]
```
## 🔹 Step 4: Configure Nginx as a Reverse Proxy

### 📄 nginx/nginx.conf
```
server {
    listen 80;

    location / {
        proxy_pass http://app:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```
## 🔹 Step 5: Create Docker Compose File

### 📄 docker-compose.yml
```
version: "3.9"
services:
  nginx:
    image: nginx:latest
    ports:
      - "8080:80"
    volumes:
      - ./nginx/nginx.conf:/etc/nginx/conf.d/default.conf
    depends_on:
      - app

  app:
    build: ./app
    expose:
      - "3000"
```

## 🔹 Step 6: Run the Application

docker compose up -d --build

## 🔹 Step 7: Verify the Setup

Check running containers


docker ps

Access the application

Open a browser and visit:

👉 http://localhost:8080

Test the API

curl http://localhost:8080/api

## 🔹 Step 8: Scale the Application (Optional)

docker compose up -d --scale app=3

To enable load balancing, update nginx.conf:
```
upstream backend {
    server app:3000;
}

server {
    listen 80;

    location / {
        proxy_pass http://backend;
    }
}
```

## 🔹 Step 9: Clean Up

docker compose down

## 🔹 Key Learning Outcomes

✅ Understand the role of a web server in dynamic content delivery

✅ Learn how Nginx acts as a reverse proxy

✅ Deploy a containerized dynamic application

✅ Use Docker Compose for multi-service orchestration

✅ Gain practical DevOps experience.


