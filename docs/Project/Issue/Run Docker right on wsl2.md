---
Created: 22:22 24-05-2024
tags:
  - issue
---
# Install docker in WSL without Docker Desktop

## Install WSL

- Open PowerShell
- Run `wsl –install`
- Restart machine
- Set username and password

## OR USE THE BEST ONE 
```shell
sudo apt update 
sudo apt install docker.io -y
sudo usermod -aG docker $USER
```



## Setup Docker

```sh
# update system
sudo apt-get update 

# install deps
sudo apt-get install ca-certificates curl gnupg lsb-release 

# import gpg
sudo mkdir -p /etc/apt/keyrings 

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg 

echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null 

sudo apt-get update 

# install docker
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin 

# start docker service
sudo service docker start 

# verify the installation 
sudo docker run hello-world 
```

## Run docker without sudo

```sh
sudo groupadd docker 

sudo usermod -aG docker $USER 
```

Restart the terminal

## Start docker service on WSL boot

```sh
sudo vim /etc/wsl.conf 
```

Paste below content

```sh
[boot] 
command="service docker start" 
```

Next time docker service will start with WSL
- https://therdnotes.com/install-docker-in-wsl-without-docker-desktop
- [Running Docker in WSL2 Ubuntu Distro without Docker Desktop | by Utkarsh Shigihalli | Medium](https://onlyutkarsh.medium.com/running-docker-in-wsl2-ubuntu-distro-without-docker-desktop-6ec495e8bb4d)
- [Using Docker and Kubernetes without Docker Desktop on Windows 11 – cuteprogramming](https://cuteprogramming.blog/2023/05/21/using-docker-and-kubernetes-without-docker-desktop-on-windows-11/)