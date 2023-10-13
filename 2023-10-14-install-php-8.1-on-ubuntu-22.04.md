---
layout: post
title: "How to Install PHP 8.1 on Ubuntu 22.04"
date: 2023-10-14 12:00:00 +0700
categories: linux php nginx
---

PHP 8.1 is the latest version of the popular server-side scripting language, bringing numerous features and improvements. In this guide, we will walk you through the steps to install PHP 8.1 on an Ubuntu 22.04 system.
We will use the Ondřej Surý's PPA repository to easily install PHP 8.1 on Ubuntu. Follow the steps below to get PHP 8.1 up and running.

## Prerequisites
Before you begin, make sure you have a user account with sudo privileges, or you are logged in as the root user.

## Step 1: Update Package List
Start by updating the list of available packages to ensure you have the latest information on software repositories and available packages.

```bash
sudo apt update
```

## Step 2: Install Software Properties Common
To add the PPA repository for PHP 8.1, you need to install the `software-properties-common` package.

```bash
sudo apt install software-properties-common -y
```

## Step 3: Add PHP Repository
Add the PPA repository maintained by Ondřej Surý for PHP.

```bash
sudo add-apt-repository ppa:ondrej/php
```

## Step 4: Update Package List Again
After adding the PHP repository, update the package list to include the new repository.

```bash
sudo apt update
```

## Step 5: Install PHP 8.1
Now that you have added the PHP repository, you can install PHP 8.1:

```bash
sudo apt install php8.1 -y
```

## Step 6: Install PHP Modules
To make the most out of PHP, you may want to install various modules commonly used in web development. You can install multiple PHP extensions in one command using a brace expansion.

```bash
sudo apt install -y php8.1-{common,cli,gd,curl,mysql,xml,mbstring,zip,ldap,xmlrpc,curl,intl,fpm,imagick,dev,imap,opcache,soap,memcached,redis}
```

## Step 7: Enable and Start PHP-FPM
PHP-FPM (PHP FastCGI Process Manager) is the preferred way to serve PHP applications with Nginx or Apache. To enable PHP-FPM and start it as a service, use the following commands:
```bash
sudo systemctl enable --now php8.1-fpm
```

## Step 8: Verify PHP-FPM Status
Check the status of the PHP-FPM service to ensure it is running without issues:

```bash
sudo systemctl status php8.1-fpm
```
If everything is set up correctly, you should see the status information, indicating that PHP-FPM is active and running.

That's it! You have successfully installed PHP 8.1 on your Ubuntu 22.04 system. You can now start developing and hosting your PHP applications with the latest features and enhancements that PHP 8.1 has to offer.
