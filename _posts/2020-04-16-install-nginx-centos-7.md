---
date: 2020-04-14
title: How to install phpMyAdmin on CentOS 7 with Nginx
categories:
  - databases
description: "How to change hostname on CentOS 7"
type: Document
---

## Prerequisites

## Step 1 - Add Nginx repository

Let's start with adding the Nginx repository. Creata the following file `/etc/yum.repos.d/nginx.repo`

~~~ bash
[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/centos/7/$basearch/
gpgcheck=1
enabled=1
~~~

Import the signing key

~~~ bash
rpm --import https://nginx.org/keys/nginx_signing.key
~~~

## Step 2 - Install Nginx webserver

~~~ bash
sudo yum install nginx
~~~ 

~~~ output
----------------------------------------------------------------------

Thanks for using nginx!

Please find the official documentation for nginx here:
* http://nginx.org/en/docs/

Please subscribe to nginx-announce mailing list to get
the most important news about nginx:
* http://nginx.org/en/support.html

Commercial subscriptions for nginx are available on:
* http://nginx.com/products/

----------------------------------------------------------------------
  Verifying  : 1:nginx-1.16.1-1.el7.ngx.x86_64                                                                                                                                                                                             1/1

Installed:
  nginx.x86_64 1:1.16.1-1.el7.ngx

Complete!
~~~

Enable Nginx webserver

~~~ bash
systemctl start nginx
~~~

~~~ bash
systemctl enable nginx
~~~

~~~ output
Created symlink from /etc/systemd/system/multi-user.target.wants/nginx.service to /usr/lib/systemd/system/nginx.service.
~~~

## Step 3 - verify

Type the IP address of your server into your favorite browser. In our case it's `185.62.56.184`. If you see the following text on your website you can verify that Nginx webserver is installed and working.

~~~ output
Welcome to nginx!

If you see this page, the nginx web server is successfully installed and working. Further configuration is required.

For online documentation and support please refer to nginx.org.
Commercial support is available at nginx.com.

Thank you for using nginx.
~~~

## Conclusion

In this article we described how you can install Nginx webserver on your CentOS 7. 
