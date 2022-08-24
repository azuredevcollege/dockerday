# Challenge 0: Prerequisites

To be able to follow all the challenges provided in this workshop, you need a few prerequisites on your machine. This challenge is for setting up your system before the workshop day. 

## Table Of Contents

1. [Git Version Control](#git-version-control)
1. [Azure CLI](#azure-cli)
1. [WSL 2](#wsl-2)
1. [Docker](#docker)
1. [Docker Hub](#docker-hub)
1. [Visual Studio Code](#visual-studio-code)

## Git Version Control

The repository is located at GitHub, so - obviously - we'll need a local _Git client_ to interact with the repository. Download and install the appropriate version of Git for you here: <https://git-scm.com/download>

## Azure CLI

We will be using the _Azure command line interface_ to create and interact with resources running in Azure.

<details>
  <summary>Click to expand!</summary>

To install it, go to <https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest> and choose your platform.

When finished, login to your Azure account from the command line:

```shell
$ az login
You have logged in. Now let us find all the subscriptions to which you have access...
```

A browser window will open, login to Azure and go back to the command prompt. Your active subscription will be shown as JSON, e.g.:

```json
{
  "cloudName": "AzureCloud",
  "id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
  "isDefault": false,
  "name": "Your Subscription Name",
  "state": "Enabled",
  "tenantId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
  "user": {
    "name": "xxx@example.com",
    "type": "user"
  }
}
```

If you have multiple subscriptions, make sure your are working with the correct one!

```shell
$ az account show
{
  "cloudName": "AzureCloud",
  "id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
  "isDefault": false,
  "name": "Your Subscription Name",
  "state": "Enabled",
  "tenantId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
  "user": {
    "name": "xxx@example.com",
    "type": "user"
  }
}
```

If that is not the correct one, follow these steps below:

```shell
$ az account list -o table
[the list of available subscriptions is printed]

$ az account set -s <SUBSCRIPTIONID_YOU_WANT_TO_USE>
```
</details>

## WSL 2

If you are running Windows 10 or Windows 11 you can install a Linux distribution by using the Windows Subsystem for Linux. This way you can use Linux tools and still be completely integrated with your Windows tools. While this is optional we highly recommend it. Follow this [link](https://docs.microsoft.com/en-us/windows/wsl/install) to install the WSL 2.


## Docker

<img src="./img/dockerlogo.png" width="200">

It's obvious that it's expected you to have Docker installed on your computer. But installation process is not as seamless as it has to be. Docker publishes different packages for different operating systems. Please follow the section of your operating system below and install related Docker package published for your operating system. 

***If you can't install any software on your computer due to company policies or other reasons, please spin up an Ubuntu VM on Azure and follow the Linux section below***

### Mac Os

Docker Desktop for Mac is available for macOS 10.13 or newer: i.e. High Sierra (10.13), Mojave (10.14) or Catalina (10.15). Mac hardware must be a 2010 or a newer model.

<details>
  <summary>Click to expand!</summary>

**Installation**
1. Visit "Docker Desktop for Mac" section of the Docker Hub -->  <https://hub.docker.com/editions/community/docker-ce-desktop-mac/>
2. Click **Get Docker** link on the right side of the page and download **Docker.dmg** file
3. Double-click **Docker.dmg** to start the install process.
4. When the installation completes and Docker starts, the whale in the top status bar shows that Docker is running, and accessible from a terminal.
<img src="https://d1q6f0aelx0por.cloudfront.net/icons/whale-in-menu-bar.png">
5. After the installation, check if everything works as expected. Open your favourite terminal application and execute the **docker version** and **docker run hello-world** commands. If you get the similar outputs as below, it means that your docker installation has been successfully completed.

```shell
$ docker version
Client: Docker Engine - Community
 Version:           ...
```
```shell
$ docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

...
```
</details>

### Windows 11
Docker Desktop for Windows is available for  Windows 10 and 11 64-bit Home, Pro, Enterprise and Education. Docker Desktop for Windows either uses Windows-native Hyper-V virtualization and networking or the WSL 2 backend. We recommend the WSL 2 for your developer machine in general. See the installation instructions above.

<details>
  <summary>Click to expand!</summary>

**Installation**
1. Visit "Docker Desktop on Windows" section of the Docker Hub -->  <https://docs.docker.com/desktop/install/windows-install/>
1. Make sure your machine is set up correctly for using either the WSL 2 backend (recommended) or the Hyper-V backend.
1. Click the **Docker Desktop for Windows** link and download the **Docker Desktop Installer.exe** file
1. Double-click **Docker Desktop Installer.exe** to run the installer.
1. When the installation finishes, Docker starts automatically. The whale <img src="https://d1q6f0aelx0por.cloudfront.net/icons/whale-x-win.png"> in the notification area indicates that Docker is running, and accessible from a terminal.
1. After the installation, check if everything works as expected. Open your Windows Powershell  terminal application and execute the **docker version** and **docker run hello-world** commands. If you get the similar outputs as below, it means that your docker installation has been successfully completed.

```shell
> docker version
Client: Docker Engine - Community
 Version:           ...
```
```shell
> docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

...
```
</details>

### Linux
Docker Engine is available on a variety of Linux platforms as a static binary installation. Docker provides **.deb** and **.rpm** packages from the following Linux distributions and architectures:
<img src="./img/dockerlinux.png">

<details>
  <summary>Click to expand!</summary>

**Installation**

Follow the instructions below to install Docker on your distro:
- https://docs.docker.com/engine/install/centos/
- https://docs.docker.com/engine/install/debian/
- https://docs.docker.com/engine/install/fedora/
- https://docs.docker.com/engine/install/ubuntu/

**Ubuntu:**

Open your terminal application and execute the following commands. 
1. Older versions of Docker were called docker, docker.io, or docker-engine. If these are installed, uninstall them:
```shell
$ sudo apt-get remove docker docker-engine docker.io containerd runc
```
2. Download and run the installation script.
```shell
$ curl -fsSL https://get.docker.com -o get-docker.sh
$ sudo sh get-docker.sh
```

3. If you would like to use Docker as a non-root user, you should now consider adding your user to the “docker” group with something like:
 ```shell
$ sudo usermod -aG docker your-user
```

4. After the installation, check if everything works as expected. On the terminal, execute the **docker version** and **docker run hello-world** commands. If you get the similar outputs as below, it means that your docker installation has been successfully completed.

```shell
$ docker version
Client: Docker Engine - Community
 Version:           ...
```
```shell
$ docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

...
```
</details>

## Docker Hub
If you didn't sign up yet, we recommend you to sign up and create your Docker ID. This will allow you to create public and private repositories to store your own Docker Images. 
- Visit <https://hub.docker.com/> and fill the form, click **Sign Up** button and create your Docker ID. 
- Check your mailbox and confirm your account creation. 

## Visual Studio Code
To work with all the samples provided in this workshop, you will need an IDE. To target a wide range of developers/architects, we will be using Visual Studio Code as it runs cross-platform. 

Therefore, go to <https://code.visualstudio.com/docs/setup/setup-overview> and install it on your machine.

### Useful Extensions ###

After the setup is complete, open "Visual Studio" and open the "Extensions" sidebar:

![Visual Studio Extensions](./img/vscode_extensions.png "VS Code Extensions")

Search and install the following extension:

- Docker for Visual Studio Code <https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker>
