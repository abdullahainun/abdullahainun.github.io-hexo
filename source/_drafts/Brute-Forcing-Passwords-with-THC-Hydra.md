title: Brute Forcing Passwords with THC-Hydra
author: Ainun Abdullah
tags:
  - devops
categories:
  - devops
date: 2019-07-20 02:48:00
---
# Apa itu Hydra

Hydra adalah alat peretas kata sandi online yang sangat cepat, yang dapat melakukan serangan kamus cepat terhadap lebih dari 50 Protokol, termasuk Telnet, RDP, SSH, FTP, HTTP, HTTPS, SMB, beberapa database, dan banyak lagi. THC (The Hackers Choice) menciptakan Hydra untuk para peneliti dan konsultan keamanan untuk menunjukkan betapa mudahnya mendapatkan akses tidak sah ke sistem dari jarak jauh.

# Installing THC-Hydra

Jika Anda menjalankan Kali Linux, Anda sudah memiliki versi Hydra yang terinstal, untuk semua sistem operasi Linux berbasis Debian lainnya unduh dari repositori dengan menggunakan.

```bash
sudo apt-get install hydra hydra-gtk
```

atau anda bisa download versi terakhir dari repository berikut https://github.com/vanhauser-thc/thc-hydra

Anda bisa clone github repository tersebut dengan perintah berikut:

```
git clone https://github.com/vanhauser-thc/thc-hydra
```

kemudian pindah direktori dengan perintah berikut:

```
cd thc-hydra
```

kemudian ketikkan perintah dibawah ini untuk configure source code

```
./configure
```
kemudian compile 
```
make
```

dan akhirnya install ke sistem.

```
sudo make install
```


source: https://www.hempstutorials.co.uk/brute-forcing-passwords-with-thc-hydra/

