---
title: "Dokku ipaddress:port based access without VHOST" 
excerpt: "A common use case is to use Dokku without an actual domain. I address how to use a consistent external port with an ip address since the docs don't."
categories:
  - DevOps
tags:
  - Docker
  - DevOps
  - Nginx
toc: true
toc_sticky: true
---
Dokku isn't clear how to host a server when you don't have a domain you want to use. If you don't enable their vhost by default then the external port of your app CHANGES EVERY DEPLOY. They only describe in detail their http://subdomain.domain.com deploy. Here I show you how to use the http://ipaddress:port deploy in a consistent manner.

*Edit:* They are now fixing the issue!!! [https://github.com/progrium/dokku/issues/1123#issuecomment-141173545 ](https://github.com/progrium/dokku/issues/1123#issuecomment-141173545 )

### Why was this so hard to figure out?
1. When I asked how to do it on Github, I didn't get an answer https://github.com/progrium/dokku/issues/1123#issuecomment-140610139
2. When I asked how to "keep a consistent port when not using vhost" in in their IRC channel #dokku I got the response "put a vhost on it". Not helpful...
3. When you don't config their vhost, nginx doesn't run. That means I spent about 1 hour configuring nginx.conf not realizing it wasn't even enabled.
4. Nginx is only enabled when NO_VHOST is set correct, VHOST and HOSTNAME files are set with the domain. Items mentioned in the documentation here http://progrium.viewdocs.io/dokku/nginx/ under "container network interface binding".
5. The docs don't make mention of this possible configuration. I guess everyone always has a domain they want to use or doesn't care when the external port changes.

### How to configure this?
1. If you already have a deployed app, delete it `dokku delete myApp`
2. add a VHOST file in your ~dokku (not to be confused with ~/dokku which is nothing)
3. add a fake domain to your HOSTNAME (fakedomain.com) file in your ~dokku directory
4. deploy your app `git remote add dokku dokku@ipaddress:myApp` `git push dokku master`
5. (optional) restart and relink your mongodb if applicable `dokku mongodb:link myApp` `dokku ps:restart myApp`
6. (optional) set extra env variables on your app `dokku config:set myApp NODE_ENV=dev`
7. change the ~dokku/myApp/nginx.conf file to 

```
server {
  listen      [::]:80;
  listen      80;
  server_name myApp.fakedomain.com ;
  access_log  /var/log/nginx/myApp-access.log;
  error_log   /var/log/nginx/myApp-error.log;

  location    / {

    gzip on;
    gzip_min_length  1100;
    gzip_buffers  4 32k;
    gzip_types    text/css text/javascript text/xml text/plain text/x-component application/javascript application/x-javascript application/json application/xml  application/rss+xml font/truetype application/x-font-ttf font/opentype application/vnd.ms-fontobject image/svg+xml;
    gzip_vary on;
    gzip_comp_level  6;

    proxy_pass  http://myApp;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection upgrade;
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_set_header X-Forwarded-For $remote_addr;
    proxy_set_header X-Forwarded-Port $server_port;
    proxy_set_header X-Request-Start $msec;
  }
  include /home/dokku/myApp/nginx.conf.d/*.conf;
}
upstream myApp {
  server 172.17.0.55:5000;
}
```

In my example nginx.conf file I will be able to always connect to the server by typing in http://myipaddress:80. Even between deployments.