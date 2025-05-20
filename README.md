🐳 Inception

Inception is a web infrastructure project built with Docker, where you create a secure, containerized environment running WordPress, MariaDB, and Nginx with HTTPS support via mkcert.

📦 Overview

This project sets up a complete web environment using Docker Compose, with the following services:

Service   | Description

Nginx     | Acts as a reverse proxy and serves HTTPS traffic

WordPress | PHP-powered CMS served via PHP-FPM

MariaDB   | Database backend for WordPress

🔐 HTTPS Support

Self-signed SSL certificates are generated using mkcert for a local domain (e.g., naadam.42.fr) during the image build process — no need for OpenSSL or Let's Encrypt.

⚙️ Environment Variables

Configure your environment using the .env file

🧪 Installation & Usage

🔧 Prerequisites

- Docker

- Docker Compose

- Make

📥 Build and Run

make

# or manually:

docker-compose up -d

The services will start in this order: mariadb → wordpress → nginx.

🔐 SSL with mkcert

Instead of OpenSSL, this setup uses mkcert to generate locally trusted development certificates:

naadam.42.fr.crt

naadam.42.fr.key

Certificates are placed in:

/etc/nginx/ssl inside the Nginx container.

🌐 Access Your Site

After running docker-compose, open:

https://naadam.42.fr

To make the domain resolve locally, add the following to your /etc/hosts:

127.0.0.1 naadam.42.fr

📁 Persistent Data

Docker bind mounts are used to persist data outside containers:

Volume	

wp-volume	/home/naadam/data/wordpress_vol	WordPress files

db-volume	/home/naadam/data/mariadb_vol	MariaDB data files

🧹 Cleaning Up

make fclean

# or manually:

docker-compose down 

This will stop all containers and remove volumes (data loss warning ⚠️).

📚 What You’ll Learn

Writing Dockerfiles for production-like services

Managing PHP + MySQL environments

Using Docker Compose for orchestration

Setting up HTTPS locally with mkcert

Volume management and persistence
