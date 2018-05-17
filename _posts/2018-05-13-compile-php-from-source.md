---
layout: post
comments: true
title: Compile PHP from source
tags: [ci, gitlab]
---

<p align="center">
  <img alt="Loading" src="https://cdn2.iconfinder.com/data/icons/designer-skills/128/code-programming-php-software-develop-command-language-512.png">
</p>

**Goal**

If you've ever wanted to get involved with PHP internals, writing tests is a great way. The tests are written in PHP so you don't even need to know C to get started.

The first step to writing tests for PHP source is downloading and compiling the PHP source code.

As a developer
I want to be able to compile php code source written in c and install php binary into `/usr/local/bin` linux binary location.

**Steps**

1. **Install the dependencies**:You'll need to install a few dependencies as `autoconf` `dpkg-dev` `file` `gcc` `g++` `libc-dev` `make` `pkg-config` `re2c` `ca-certificates` `curl` `xz-utils` `bison` `libxml2-dev`

2. **Clone the php-src repository**:We'll be cloning the code php-src Github repository and switch to php-src folder to checkout tag
 
 ```
  git clone https://github.com/php/php-src.git
 
  cd php-src
 
  git checkout tags/php-7.2.5
 ```

3. **Configure and make**:Since the repo doesn't contain a configure script, we'll need to build it first and execute this shell script file
 
  `./buildconf`

 we should have a new generated shell script file called configure, launch this script as follow
  `./configure`

 we should have a new generated file called Makefile. 
   
  Compile the source code with `make`  and install php binary in system by taping `sudo make install`

4. **Verifiying installation**:Make sure by taping `/usr/local/bin/php --version` that php is correctly installed globally

Please follow this link [compile_php.sh](https://github.com/dridi-sirine/compile_php).
