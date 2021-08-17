title: Hack RDP windows dengan RDPWrap
author: Ainun Abdullah
tags: []
categories:
  - Infrastructure
date: 2018-12-18 20:53:00
---
windows adalah salah satu sistem operasi yang banyak digunakan saat ini, terutama untuk keperluan perkantoran maupun yang lain. salah satu fitur yang banyak digunakan pada jaringan lokal maupun public adalah remote desktop protokol (rdp). yang mana dapat digunakan untuk remote sistem operasi windows dari jaringan. 
<!--more-->
namun, pada windows biasa(pro, home, education, dll) tidak dapat digunakan rdp secara multiremote. atau bisa dibilang 1  os windows tersebut hanya bisa di remote oleh 1 user dalam satu waktu. 

nah, di sini saya ingin berbagi bagaimana caranya agar windows kita dapat digunakan remote desktop dengan multiuser. beberapa bulan yang lalu saya menemukan aplikasi bernama rdpwrap yang dapat digunakan untuk mengatasi hal tersebut. 

- download aplikasi di  https://github.com/stascorp/rdpwrap/releases

- pilih format .msi atau .zip

- kemudian install aplikasi tersebut, dengan cara klik 2x install.bat 
- check apakah aplikasi sudah terpasang atau belum dengan menjalankan RDPcheck.exe
- restart windows anda
- cobalah konek ke windows anda dengan multiuser via rdp