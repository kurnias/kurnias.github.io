---
layout: post
title: "How to Set Up SSH Key Authentication for Secure Remote Access"
date: 2023-08-22 12:00:00 +0700
categories: linux ssh security
---

SSH key authentication provides a secure and convenient way to access remote servers without the need for passwords. In this guide, we'll walk you through the process of generating an SSH keypair on a Linux machine and using it to connect to a remote VPS server from a Windows desktop using PuTTY.

## Prerequisites

- A Linux machine (to generate the SSH keypair).
- A Windows desktop with PuTTY installed.

## Step 1: Generate SSH Keypair on Linux

1. Open a terminal on your Linux machine.
2. Run the following command to generate an SSH keypair:
   ```
   ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ```
3. Provide an optional passphrase for added security (or press Enter for no passphrase).

## Step 2: Copy Public Key to VPS Server

1. Using the `ssh-copy-id` command (or manually), append the contents of the `id_rsa.pub` file to the `~/.ssh/authorized_keys` file on your VPS server.
2. Set appropriate permissions for the `~/.ssh` directory and the `authorized_keys` file on the server:
   ```
   ssh user@vps_server_ip "chmod 700 ~/.ssh"
   ssh user@vps_server_ip "chmod 600 ~/.ssh/authorized_keys"
   ```

## Step 3: Convert Private Key for PuTTY

1. Open PuTTYgen on your Windows desktop.
2. Click "Load" and select your `id_rsa` private key.
3. Click "Save private key" to convert the private key to PuTTY format (`.ppk`).

## Step 4: Configure PuTTY and Connect

1. Open PuTTY on your Windows desktop.
2. In the "Session" category, enter the VPS server's IP address or hostname.
3. In the "Connection" > "SSH" > "Auth" category, browse and select the converted `.ppk` private key.
4. Save the session settings if desired.
5. Click "Open" to initiate the SSH connection.

## Conclusion

By following these steps, you've successfully set up SSH key authentication for secure remote access to your VPS server. Your private key remains secure on your Windows desktop, and the public key is safely stored on the VPS server, ensuring a secure and password-free connection.

Remember to keep your private key secure and never share it with anyone. With SSH key authentication, you can enjoy enhanced security and streamlined remote server access.

