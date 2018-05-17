---
layout: post
comments: true
title: How to specify and setup lemp stack using serverspec and shell
tags: [tdi, serverspec, lemp]
---

<p align="center">
  <img alt="Loading" src="https://d3ohwog8xeymzc.cloudfront.net/wp-content/uploads/2017/01/28110822/lemp-ubuntu.jpg">
</p>

**Goal**

The LEMP software stack is a group of software that can be used to serve dynamic web pages and web applications. This is an acronym that describes a Linux operating system, with an Nginx web server. The backend data is stored in the MySQL database and the dynamic processing is handled by PHP.

**Serverspec Specification**

_Nginx_

  ```
  describe service('nginx') do
    it { should be_enabled }
  end
  describe package('nginx') do
    it { should be_installed }
  end
  describe service('nginx') do
    it { should be_running }
   end
  describe port(80) do
    it { should be_listening }
  end
  ```
_MYSQL_

  ```
  describe package('mysql') do
    it { should be_installed }
  end
  describe service('mysql') do
    it { should be_running }
  end
  ```
_PHP_

  ```
   describe package('php') do
     it { should be_installed }
   end
  ```

**Provisionning**
1. Install the Nginx Web Server
2. Install MySQL to Manage Site Data
3. Install PHP for Processing
4. Configure Nginx to Use the PHP Processor
5. Create a PHP File to Test Configuration
