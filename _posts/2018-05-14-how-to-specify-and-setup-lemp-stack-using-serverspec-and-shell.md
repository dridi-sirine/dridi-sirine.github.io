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
  describe 'MySQL config parameters' do
    context mysql_config('innodb-buffer-pool-size') do
      its(:value) { should > 100000000 }
    end

    context mysql_config('socket') do
      its(:value) { should eq '/tmp/mysql.sock' }
    end
  end
  ```
_PHP_

  ```
  describe 'PHP config parameters' do
    context  php_config('default_mimetype') do
      its(:value) { should eq 'text/html' }
    end

    context php_config('session.cache_expire') do
      its(:value) { should eq 180 }
    end

    context php_config('mbstring.http_output_conv_mimetypes') do
      its(:value) { should match /application/ }
    end
  end
  ```

**Provisionning**
1. Install the Nginx Web Server
2. Install MySQL to Manage Site Data
3. Install PHP for Processing
4. Configure Nginx to Use the PHP Processor
5. Create a PHP File to Test Configuration
