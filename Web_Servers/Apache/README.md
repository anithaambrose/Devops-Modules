# Apache HTTP Server

## 📌 Overview

Apache HTTP Server (often called Apache or httpd) is one of the oldest and most widely used open-source web servers. It is known for its flexibility and extensive module ecosystem.

## 🏗️ Architecture

Process/Thread-based (MPM – Multi-Processing Modules)

## Supports different modes:

  Prefork – Process-based, stable, used with mod_php
  
  Worker – Thread-based, better performance
  
  Event – Improved handling of concurrent connections

## ✅ Key Features

  Serves both static and dynamic content
  
  Supports .htaccess for per-directory configuration
  
  Rich module ecosystem (mod_php, mod_ssl, mod_rewrite)
  
  Strong community support
  
  Cross-platform (Linux, Windows, macOS)

## 🔧 Handling Dynamic Content

Apache can directly execute dynamic content using modules:

   PHP via mod_php
   
   Python via mod_wsgi
   
   Perl via mod_perl

## 📄 Example Configuration
```
<VirtualHost *:80>
    ServerName example.com
    DocumentRoot /var/www/html

    <Directory /var/www/html>
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```
## 📊 Use Cases
  Shared hosting environments
  
  PHP-based applications (e.g., WordPress, Drupal)
  
  Legacy systems requiring .htaccess

## ⚖️ Apache vs Nginx
  |Feature |	Apache	|Nginx|
  |---------|---------|------|
  |Architecture |	Process/Thread-based|	Event-driven|
  |.htaccess Support|	✅ Yes	|❌ No|
  |Static Content Performance	|Good|	Excellent|
  |High Concurrency|	Moderate	|Excellent|
  |Reverse Proxy	|Supported	|Excellent|

## 🏆 When to Use Apache

  When .htaccess flexibility is required.
  
  For legacy PHP applications.
  
  In shared hosting environments.

# Apache Tomcat

## 📌 Overview

Apache Tomcat is not a traditional web server; it is a Java Servlet container and application server used to run Java-based web applications.

## 🏗️ Architecture

  Implements Java Servlet, JSP (JavaServer Pages), and WebSocket specifications.
  
  Uses a thread-based request handling model.
  
  Often deployed behind a reverse proxy like Nginx or Apache.

## ✅ Key Features

  Optimized for Java applications
  
  Lightweight compared to full Java EE servers
  
  Built-in session management
  
  Supports WAR (Web Application Archive) deployment
  
  Easy integration with CI/CD pipelines

## 🔧 Example Workflow

Client → Nginx/Apache → Tomcat → Java Application

## 📄 Default Ports
|Port|	Purpose|
|----|-------|
|8080	|HTTP|
|8443|	HTTPS|
|8009	|AJP Connector|
|8005	|Shutdown Port|
## 📄 Example server.xml Connector

```
<Connector port="8080" protocol="org.apache.coyote.http11.Http11NioProtocol"
           connectionTimeout="20000"
           redirectPort="8443" />
```
## 📊 Use Cases

  Spring Boot applications
  
  Enterprise Java applications
  
  Microservices in Java ecosystems

## 🏆 When to Use Tomcat

  When deploying Java-based applications.
  
  In enterprise environments.
  
  When WAR file deployment is required.

