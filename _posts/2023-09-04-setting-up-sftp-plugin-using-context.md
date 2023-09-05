---
layout: post
title: "Setting Up SFTP Plugin VS Code with Multiple SFTP Servers"
date: 2023-09-04 12:00:00 +0700
categories: ssh vscode
---

Using the SFTP (SSH File Transfer Protocol) plugin in Visual Studio Code can greatly enhance your development workflow by allowing you to easily transfer files between your local machine and remote servers. In this tutorial, we will show you how to set up the SFTP plugin in VS Code to work with two different SFTP servers, all from a Windows environment.

## Prerequisites

Before we begin, make sure you have the following:

- [Visual Studio Code](https://code.visualstudio.com/) installed on your Windows machine.
- The [SFTP plugin](https://marketplace.visualstudio.com/items?itemName=liximomo.sftp) installed in your VS Code.

## Configuring SFTP for Multiple Servers using context

We'll use a JSON configuration file to set up profiles for our SFTP servers. The configuration you provided in your question is an excellent starting point. Here's a breakdown of the essential properties:

- `"name"`: A descriptive name for your profile.
- `"host"`: The hostname or IP address of the remote server.
- `"context"`: The local directory path where you want to work for this profile.
- `"protocol"`: Set to `"sftp"` for SFTP connections.
- `"port"`: The SFTP port (usually 22).
- `"secure"`: Set to `true` for secure SFTP connections.
- `"username"`: Your username for the remote server.
- `"remotePath"`: The path on the remote server where you want to transfer files.
- `"password"` or `"privateKeyPath"`: Depending on your authentication method (password or SSH key).
- `"uploadOnSave"`: Set to `false` if you want to manually upload files on save.

Please remember context must not be the same.

### Example Configuration

Here's an example configuration for two SFTP servers:

```json
[
    {
        "name": "Production Server",
        "host": "host1.example.com",
        "context": "C:\\Users\\foobar\\Documents\\Workspace\\htdocs",
        "protocol": "sftp",
        "port": 22,
        "secure": true,
        "username": "admin",
        "remotePath": "/var/www/example.com/htdocs",
        "password": "password",
        "uploadOnSave": false
    },
    {
        "name": "Development Server",
        "context": "C:\\Users\\foobar\\Documents\\Workspace\\src",
        "remotePath": "/home/foobar",
        "host": "host2.example.com",
        "username": "foobar",
        "privateKeyPath": "C:\\Users\\foobar\\Documents\\ssh\\foobar.pem",
        "port": 22,
        "protocol": "sftp",
        "uploadOnSave": false
    }
]

```

That's it!
