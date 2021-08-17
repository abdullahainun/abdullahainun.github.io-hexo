title: laporan footprinting
tags:
  - NetworkSecurity
  - Laporan Kuliah
categories:
  - Infrastructure
date: 2018-08-30 19:44:51
---
# laporan footprinting Praktikum Keamanan Jaringan (Tugas 1)
## identitas mahasiswa
- Nama    = Ainun Abdullah
- NRP     = 2110151049
- Kelas   = 4 D4 IT B
- MatKul  = Praktikum Keamanan jaringan
- Dosen   = Dr. Idris Winarno. S.ST, M.Kom

## content
Pada praktikum kali ini saya melakukan footprinting dengan tools nslookup dan whois
<!--more-->
nslookup adalah suatu tool untuk melihat query DNS Server yg digunakan dan juga untuk melihat IP Address suatu domain maupun sebaliknya contoh penggunaan nslookup pada percobaan ini adalah ``nslookup www.infoglobal.co.id``
<!-- more -->


```
root@ubuntu-s-1vcpu-1gb-sgp1-01:~# nslookup infoglobal.co.id
Server:     67.207.67.2
Address:    67.207.67.2#53

Non-authoritative answer:
Name:   infoglobal.co.id
Address: 117.102.76.180

Server:     67.207.67.2
Address:    67.207.67.2#53

Non-authoritative answer:
Name:   infoglobal.co.id
Address: 117.102.76.180

# whois infoglobal.co.id
```

pada percobaan diatas, setelah kita melakukan nslookup pada domain tujuan. nslookup akan memberikan jawaban berupa ip 117.102.76.180 dari domain infoglobal.co.id yang menjadi objek percobaan.

untuk melakukan mengetahui informasi lebih lanjut tentang domain infoglobal.co.id saya menggunakan tools whois. adapaun kegunaan whois adalah sebagai berikut :

- Mendukung keamanan dan kestabilan dari internet dengan menyediakan informasi kontak yang bisa dihubungi yang berhubungan dengan jaringan, ISP, dan pemilik domain.
- Untuk mendapatkan informasi ketersediaan domain. Sehingga jika domain tersedia dalam artian belum diregistrasi oleh orang lain, maka Anda bisa melakukan registrasi atas nama domain tersebut.
- Mempermudah penegakan hukum dalam investigasi pelanggaran hukum dalam suatu negara, seperti terorisme, pornografi, perdagangan organ, dan illegal content.
- Memfasilitasi pencarian data untuk hak cipta dan merk dagang Memberikan kontribusi pada kepercayaan pengunjung ketika mengunjungi suatu situs, seperti situs ecommerce ( toko online ), lembaga sosial, atau perusahaan yang menawarkan produk jasa.

baik. langsung saja. kita coba menggunakan perintah whois dengan perintah berikut ini.

```
root@ubuntu-s-1vcpu-1gb-sgp1-01:~# whois 117.102.76.180

```

output dari perintah di atas akan menampilkan beberapa informasi mengenai ip tersebut. 
```
% [whois.apnic.net]
% Whois data copyright terms    http://www.apnic.net/db/dbcopyright.html

% Information related to '117.102.64.0 - 117.102.127.255'

% Abuse contact for '117.102.64.0 - 117.102.127.255' is 'abuse@biz.net.id'

inetnum:        117.102.64.0 - 117.102.127.255
netname:        BIZNET-ID
descr:          Biznet ISP
descr:          Internet Service Provider
descr:          Jakarta, Indonesia
country:        ID
admin-c:        AA590-AP
tech-c:         AA590-AP
remarks:        Send SApam & Abuse report to: abuse@biz.net.id
status:         ALLOCATED PORTABLE
mnt-by:         MNT-APJII-ID
mnt-lower:      MAINT-ID-BIZNET
mnt-irt:        IRT-BIZNET-ID
last-modified:  2011-02-07T07:49:09Z
source:         APNIC

irt:            IRT-BIZNET-ID
address:        Biznet Networks
address:        Midplaza 2, 8th Floor
address:        Jl. Jend Sudirman Kav 10-11
address:        Jakarta 10220
e-mail:         agus_ariyanto@biz.net.id
abuse-mailbox:  abuse@biz.net.id
admin-c:        AA590-AP
tech-c:         AA590-AP
auth:           # Filtered
mnt-by:         MAINT-ID-BIZNET
last-modified:  2018-05-31T22:29:06Z
source:         APNIC

person:         Agus Ariyanto
nic-hdl:        AA590-AP
e-mail:         agus_ariyanto@biz.net.id
address:        Midplaza 2, 8th Floor
address:        Jl. Jend Sudirman Kav 10-11
address:        Jakarta, Indonesia
phone:          +62-21-57998888
fax-no:         +62-21-5700580
country:        ID
mnt-by:         MAINT-ID-BIZNET
last-modified:  2008-09-04T07:54:14Z
source:         APNIC

% Information related to '117.102.76.176 - 117.102.76.183'

inetnum:        117.102.76.176 - 117.102.76.183
netname:        BIZNET-PT-InfoGlobal-Teknologi-Semesta-BLOCK
country:        ID
descr:          PT InfoGlobal Teknologi Semesta - Surabaya
admin-c:        AA590-AP
tech-c:         AA590-AP
mnt-irt:        IRT-BIZNET-ID
status:         ASSIGNED NON-PORTABLE
mnt-by:         MAINT-ID-BIZNET
last-modified:  2017-10-21T00:44:02Z
source:         IDNIC

irt:            IRT-BIZNET-ID
address:        Biznet Networks
address:        Midplaza 2, 8th Floor
address:        Jl. Jend Sudirman Kav 10-11
address:        Jakarta 10220
e-mail:         agus_ariyanto@biz.net.id
abuse-mailbox:  abuse@biz.net.id
admin-c:        AA590-AP
tech-c:         AA590-AP
auth:           # Filtered
mnt-by:         MAINT-ID-BIZNET
last-modified:  2017-10-24T02:31:22Z
source:         IDNIC

person:         Agus Ariyanto
nic-hdl:        AA590-AP
e-mail:         agus_ariyanto@biz.net.id
address:        Midplaza 2, 8th Floor
address:        Jl. Jend Sudirman Kav 10-11
address:        Jakarta, Indonesia
phone:          +62-21-57998888
fax-no:         +62-21-5700580
country:        ID
mnt-by:         MAINT-ID-BIZNET
last-modified:  2008-09-04T07:54:14Z
source:         IDNIC

% This query was served by the APNIC Whois Service version 1.88.15-46 (WHOIS-JP3)
```

dari banyaknya informasi di atas. ada beberapa hal dapat kita simpulkan seperti berikut :

- domain infoglobal.co.id memiliki ip 117.102.76.180
- informasi whois di atas di ambil dari registra APNIC
- ISP yang digunakan adalah Biznet ISP
- Negara bagian ip tersebut terletak di Indonesia
- Domain ini Dibuat pada tahun 2008
- Nama Perusahaan yang mempunyai domain ini adalah PT InfoGlobal Teknologi Semesta - Surabaya
- Orang Yang bertanggung jawab dari pihak Biznet adalah Agus Ariyanto
- dll

Download PDF  {% asset_link footprinting.pdf disini %}