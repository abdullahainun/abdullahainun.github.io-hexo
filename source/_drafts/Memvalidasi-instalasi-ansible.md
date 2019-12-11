title: Memvalidasi instalasi ansible
author: Ainun Abdullah
tags:
  - ansible
categories:
  - devops
date: 2019-06-29 08:25:00
---
- cek versi ansible
```bash
$ ansible --version
```
+ file konfigurasi ansible memiliki empat tempat seperti berikut, dimana urutan pembacaan konfigurasi dimulai dari atas
 - ANSIBLE_CONFIG
 - ./ansible.cfg
 - ~/.ansible.cfg
 - /etc/ansible/ansible.cfg

- perintah untuk mengecek koneksi ke host
```bash
$ ansible all -m ping
```
