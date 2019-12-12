title: How to install Docker in Ubuntu 18.04

thumbnail: https://pbs.twimg.com/profile_images/1145722943688699904/n4u37v9t_400x400.png

author: Ainun Abdullah
tags:

  - devops
  - docker
  - cloud computer
  - ubuntu
categories:
  - devops
date: 2019-12-11 16:53:00
---
Untuk menginstall docker pada ubuntu 18.04, ikuti urutan perintah di bawah ini:

1. Update repository list

   ```bash
   sudo apt update
   ```

2. Install packgae requirements

   ```bash
   sudo apt install apt-transport-https ca-certificates curl software-properties-common -y3. 
   ```

   <!--more-->

3.  Add repository docker to system

   ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
   sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
   sudo apt update
   ```

4. Check docker found in our repository or yet

   ```
   apt-cache policy docker-ce
   ```
   
5. Install docker

   ```
   sudo apt install docker-ce -y
   ```

6. Check docker status

   ```
   sudo systemctl status docker
   ```

7. Add our user to docker group

   ```
   sudo usermod -aG docker ${USER}
   sudo usermod -aG docker username
   ```

   