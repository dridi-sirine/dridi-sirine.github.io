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

In order to compile a specific version of PHP from source in Github,
As a developer
I want to be able to compile php code source written in c and install php binary into `/usr/local/bin` linux binary location

**Steps**

1. Clone php-src Github repository locally using linux commands as below, don't forget to switch to php-src folder and checkout tag
`/usr/bin/git clone -b 'php-7.2.5' --single-branch https://github.com/php/php-src.git && cd $(basename $_ .git)`

2. Locate in php-src folder buildconf file and execute this shell script file `./buildconf`

3. After step 2, we should have a new generated shell script file called configure, launch this script as follow `./configure`

4. After step 3, we should have a new generated file called Makefile, you have to tape `make` to start compilation

5. Now we have compiled php in the current folder to install php binary in system, tape `sudo make install`

6. Make sure by taping `/usr/local/bin/php --version` that php is correctly installed globally

Please follow this link [compile_php.sh](https://github.com/dridi-sirine/compile_php)
