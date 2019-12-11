title: Docker and iptables
author: Ainun Abdullah
tags:
  - docker
categories:
  - devops
date: 2019-12-01 06:47:00
---
Di Linux, Docker memanipulasi rules `iptables` untuk menyediakan isolasi jaringan atau control access.

## Menambahkan policies sebelum docker rules

Secara default, semua ip dari luar di izinkan terhubung ke docker domain. jika hanya ingin menginzinkan ip tertentu yang dapat mengakses container, perlu di tambahkan rule  pada docker filter paling atas. aturan berikut membatasi akses dari luat ke semua ip address kecuali 192.168.1.1
<!--more-->
```bash
$ iptables -I DOCKER-USER -i ext_if ! -s 192.168.1.1 -j DROP
```

ext_if diatas adalah nama interface yang terdapat pada host.  jika ingin memodifikasi rule diatas menjadi subnet. maka rule yang digunakan menjadi seperti ini:

```bash
$ iptables -I DOCKER-USER -i ext_if ! -s 192.168.1.0/24 -j DROP
```

iptables juga dapat digunakan untuk mengatur berdasarkan range ip seperti ini:

```bash
$ iptables -I DOCKER-USER -m iprange -i ext_if ! --src-range 192.168.1.1-192.168.1.3 -j DROP
```

Source : https://docs.docker.com/network/iptables/