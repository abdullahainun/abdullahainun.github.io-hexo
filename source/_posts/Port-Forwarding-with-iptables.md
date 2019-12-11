title: Port Forwarding with iptables
author: Ainun Abdullah
tags:
  - linux
  - port-forwarding
categories:
  - linux
date: 2018-12-31 22:52:00
---
Assalamu'alaikum wr wb guys, di malam pergantian tahun 2018 ke 2019 ini aku mau share ilmu tentang port forwarding pada sistem operasi linux.. 

<!--more-->
Apa itu Port Forwarding ?

![port forwarding](/images/port_forwarding.png)

Jadi gini guys, Port forwarding memungkinkan komputer yang jauh untuk terhubung dengan komputer atau layanan tertentu di jaringan wilayah lokal (LAN) pribadi. Untuk koneksi yang lebih cepat, beberapa aplikasi P2P (seperti BitTorrent) mungkin juga memerlukan pengaturan Port Forwarding. Anda dapat membuka beberapa port atau jangkauan port dalam router, dan mengalihkan data melalui port tersebut ke satu klien dalam jaringan Anda.

Ketika menkonfigurasi port forwarding, administrator jaringan menyisihkan satu nomor port komunikasi pada gateway untuk penggunaan khusus berkomunikasi dengan layanan di jaringan internal, host external harus tahu nomor port ini dan alamat gateway untuk berkomunikasi dengan layanan jaringan internal.  Nomor port yang seringkali digunakan adalah nomor port 80 untuk layanan web (HTTP) pada port forwarding, sehingga layanan jaringan lokal juga dapat digunakan oleh host jaringan luar.


nah kali ini, kita akan mencoba menggunakan port forwarding pada sistem operasi linux dan iptables. iptables yaitu aplikasi berbasis linux yang digunakan untuk firewall. firewall di sini digunakan untuk mengatur paket yang boleh masuk dan keluar dari sistem.

berikut adalah contoh kita mengarahkan port 27017 ke komputer public di arahkan ke ip 192.168.0.67 dan port 27015

1. enable ip forwarding
```
# echo 1 > /proc/sys/net/ipv4/ip_forward
```
2. membuat port role redirection
```
# iptables -t nat -A PREROUTING -p tcp --dport 27017 \
   -j DNAT --to-destination 192.168.0.69:27015
```
3. membaut rule masquerade pada paket yang di kembalikan
```
iptables -t nat -A POSTROUTING -p tcp --dport 27015 -j MASQUERADE
```