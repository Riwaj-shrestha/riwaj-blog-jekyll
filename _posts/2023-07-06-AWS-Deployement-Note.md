---
layout: post
title:  "Setting Up an Ubuntu Server with NGINX, MySQL, Node.js, Git, Docker, and SSL in AWS EC2 Instance"
date:   2023-07-06 13:35:41 +0545
categories: Deployment
tags: [Deployment, AWS]
readtime: true
thumbnail-img: /assets/img/cloud-server-thumb.jpg
---
In this post, we will guide you through the process of creating an instance on Amazon EC2, configuring it with an Ubuntu server, and installing various essential components like NGINX, MySQL, Node.js, Git, Docker, and SSL certificates. By following these step-by-step instructions, you'll be able to set up a robust web server environment for hosting your applications. Let's dive in and get started!

#### CREATING INSTANCE

1. Move to EC2 
2. Click on Launch instances 
3. Select free tier ubuntu server / any other as required 
4. Storage change to 30G 
5. Review and Launch 
6. Then download pem file



#### INSTALLING NGINX

1. Login to server with pem file 
2. Make sure your pc is update:
   ```sudo apt update```
3. install nginx
   ```sudo apt install nginx -y```
4. Adjust firewall
   ```sudo ufw app list``` => will list the application profiles 
5. Make sure to allow http from security groups.
   - Add HTTP to be allowed.
   ```sudo ufw allow 'Nginx HTTP'```
   (IF NEEDED DO THAT FOR HTTPS AS WELL)
6. Now get your public url
   ```curl -4 icanhazip.com```
7. Now hit the given url and you should be able to see welcome to nginx screen

#### MYSQL

1. Install mysql server
   ```sudo apt install mysql-server```
2. Configuring mysql
   ```sudo mysql_secure_installation```
   - Agree terms 'Y'
   - ```SELECT PASSWORD LEVEL => 1 (medium) (p@ssw0rd)```
3. Accept the changes as given 
4. Now login to mysql with sudo as previosuly given password won't work
   ```sudo mysql```
5. Create user
   ```CREATE USER 'trackify'@'localhost' IDENTIFIED BY 'p@ssw0rd';```
6. Grant all privileges:
   ```GRANT ALL PRIVILEGE ON *.* TO trackify@localhost;```
7. Flush privileges:
   ```FLUSH PRIVILEGES;```

#### NODE JS

1. Install node using NVM
   - ```curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh```
   - ```curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash```
   - ```source ~/.bashrc```
   - ```nvm list-remote```
   - ```nvm install``` v16 (lts will automatically be installed)

#### GIT

1. ```git -v```
2. ```sudo apt install git```  if not found

#### DOCKER

- ```sudo apt install apt-transport-https ca-certificates curl software-properties-common```

- ```curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -```

- ```sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"```


- ```apt-cache policy docker-ce```

- ```sudo apt install docker-ce```

- ```sudo systemctl status docker```

- ```REMOVE SUDO ON DOCKER```
- ```sudo usermod -aG docker $USER```

NOW LOGOUT AND LOG BACK IN (exit and connect to server)

- ```sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose```

- ```sudo chmod +x /usr/local/bin/docker-compose```



#### ADD YARN:

- ```curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -```

- ```echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list```

- ```sudo apt update```

- ```sudo apt install yarn```



#### REACT Deployment: (NGINX)

````
location / {
try_files $uri /index.html;
}
````





#### ADDING SSL:

- ```sudo apt install certbot python3-certbot-nginx```
- ```Install certbot```
- ```sudo certbot --nginx -d example.com -d www.example.com```



