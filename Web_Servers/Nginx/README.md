# NGINX

Nginx is an open source , high-performance web server that can function as a 

1. Web Server
2. Reverse Proxy
3. Load Balancer
4. SSL/TLS Terminator
5. HTTP Cache


1. Nginx works on **Event-driven Asynchronous Architecture**, that allows it to efficiently handle thousands of **concurrent connections**, ideal for **Modern web content** such as

  HTML 
  CSS
  Javascript
  Images & Videos 
```
server {
    listen 80;
    server_name example.com;

    location / {
        root /var/www/html;
        index index.html;
    }
}
``` 
## What Is a Reverse Proxy?

A reverse proxy is a server that sits in front of one or more backend servers (such as Docker containers) and forwards client requests to those servers. The client interacts only with the reverse proxy and is unaware of the backend services.

### Benefits of Reverse Proxy

🔒 Security	Hides backend servers and enables centralized protection

⚖️ Load Balancing	Distributes traffic across multiple instances

🔐 SSL Termination	Manages HTTPS certificates

🚀 Performance	Supports caching and compression

🌐 Simplified Access	Single public endpoint

🔀 Flexible Routing	Path- and host-based routing


2. Nginx works best as a reverse proxy, where the client communicates with nginx server , while the backend service remains hidden, offering security
```
server {
    listen 80;

    location / {
        proxy_pass http://backend:3000;
    }
}
```
3. Nginx distributes incoming traffic across multiple backend servers to improve scalability and availability.

   Load balancing Methods -Round Robin (default)
```
    upstream backend_servers {
    server app1:3000;
    server app2:3000;
}

server {
    listen 80;

    location / {
        proxy_pass http://backend_servers;
    }
}
```
4. Nginx can handle HTTPS encryption, offloading this responsibility from backend servers.

```
server {
    listen 443 ssl;
    server_name example.com;

    ssl_certificate /etc/nginx/ssl/cert.pem;
    ssl_certificate_key /etc/nginx/ssl/key.pem;

    location / {
        proxy_pass http://backend:3000;
    }
}
```


## Installing Nginx 

sudo apt update

sudo apt install nginx

sudo systemctl start nginx

sudo systemctl enable nginx

## Nginx - default.conf file structure

## Directive	& Purpose

1. events	- Connection processing
2. http	 - HTTP server configuration
3. server	- Virtual host definition
4. location	- Request routing rules
5. upstream	- Backend server group

## nginx with docker

docker run -d -p 80:80 --name nginx nginx

## Nginx in a Docker Environment

###  Example: Running Nginx as a Reverse Proxy
```
version: "3.9"
services:
  nginx:
    image: nginx:latest
    ports:
      - "80:80"
    volumes:
      - ./nginx.conf:/etc/nginx/conf.d/default.conf
    depends_on:
      - app

  app:
    image: my-app
    expose:
      - "3000"
```
## Flow of Traffic

Client → Nginx (Port 80) → Application Container (Port 3000)

```

            Internet
                |
        +----------------+
        |     Nginx      |
        | Reverse Proxy  |
        +----------------+
           /      |      \
          /       |       \
     App 1     App 2     App 3
```

