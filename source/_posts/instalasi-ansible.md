title: instalasi ansible
author: Ainun Abdullah
tags:
  - ansible
  - instalasi ansible
categories:
  - devops
date: 2019-06-28 23:29:00
---
Ansible merupakan automation tool untuk manage banyak remote hosts dari single machine. kali ini aku mau sharing tentang contoh sederhana penerapan tool yang satu ini.. `check this out...`
<!--more-->
1. konfigurasi akses ssh
pertama adalah generate ssh keygen pada ansible server
```bash
$ ssh-keygen
```
 kemudian copy public ssh key ke semua remote hosts yang terhubung melalui ssh
```bash
$ ssh-copy-id -i ~/.ssh/id_rsa.pub samdon@host1
$ ssh-copy-id -i ~/.ssh/id_rsa.pub samdon@host2
```
2. instalasi ansible pada ubuntu 16.04
```bash
$ sudo apt-add-repository ppa:ansible/ansible
$ sudo apt update
$ sudo apt install ansible
```
 pada step ini, ansible server telah terinstall. untuk mengeceknya bisa menggunakan perintah berikut :
```
$ ansible --version
```
3. konfigurasi hosts dan groups
`/etc/ansible/hosts` merupakan file yang digunakan untuk mengatur host yang terhubung pada server ansible. untuk mengeditnya dapat menggunakan perintah berikut ini :
```bash
$ sudo nano /etc/ansible/hosts
```
 kemudian sebagai contoh host dapat diatur dalam group-group yang diinginkan seperti berikut :
```bash
[webservers]
web-host1
web-host2

[dbservers]
db-host1
```
4. test ansible setup
```bash
$ ansible -m ping all
```
 ```bash
$ ansible -m ping web-host1        ## Specific host 
$ ansible -m ping webservers       ## Specific group 
```
 ```bash
$ ansible -m shell -a 'free -m' web-host1
```
source : https://tecadmin.net/install-ansible-on-ubuntu-16-04-xenial/