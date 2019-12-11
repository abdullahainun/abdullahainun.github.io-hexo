title: web scraping menggunakan  BeautifulSoup python
author: Ainun Abdullah
tags:
  - web scraping
categories:
  - python
date: 2019-05-06 10:59:00
---
Assalamu'alaikum wr wb. selamat pagi temen - temen. semoga kalian dalam keadaan sehat wal afiat. kali ini kita akan membahas mengenai web scraping dengan menggunakan bahasa pemrogaman python. baik kita mulai artikel ini dengan pembahasan mengenai apa itu web scraping, Web scraping (panen web) adalah pengambilan sebuah dokumen semi-terstruktur dari internet, umumnya berupa halaman-halaman web dalam bahasa markup seperti HTML atau XHTML, dan menganalisis dokumen tersebut untuk diambil data tertentu dari halaman tersebut. Istilah gampangnya yaitu pengambilan konten atau sebagian data dari suatu situs web untuk penjelasan lebih detail temen-temen bisa membacanya [disini](https://pesonainformatika.com/other-notes/apa-itu-web-scraping/)

Tahap pertama yang harus dilakukan supaya teman-teman dapat lebih jauh belajar web scraping adalah menggunakan library requests seperi contoh source code dibawah ini.
<!--more-->
```python
import requests
page = requests.get("http://dataquestio.github.io/web-scraping-pages/simple.html")
page
```
respone yang didapat dari script di atas adalah seperti di bawah ini
```
<Response [200]>
```
angka 200 menunjukan bahwa halaman berhasil didownload.
untuk eksperimen lainnya bisa juga menggunakan page.content yang digunakan untuk menampilkan isi dari halaman yang didownload
```python
page.content
```
```python
b'<!DOCTYPE html>\n
<html>\n
    <head>\n
        <title>A simple example page</title>\n
    </head>\n
    <body>\n
        <p>Here is some simple content for this
 page.</p>\n
    </body>\n
</html>'
```
# web scraping using BeautifulSoup

Pada artikel ini library yang kita gunakan adalah [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) untuk melakukan web scraping pada contoh kasus blog saya https://abdullahainun.me. 
```python
import requests
from bs4 import BeautifulSoup
import pandas as pd
page = requests.get("https://abdullahainun.github.io")
soup = BeautifulSoup(page.content, 'html.parser')
main = soup.find(id="main")
main_juduls = main.select(".article-title")
juduls = [a.get_text() for a in main_juduls]
href = [a.get('href') for a in main_juduls]
dfBlog = pd.DataFrame({
        "judul": juduls,
        "link" : href
    })
print(dfBlog)
```
jadi setelah kita mendapatkan text yang kita inginkan kita parsing datanya ke dataframe sehingga output yang didapatkan menjadi seperti ini :
```
                                               judul                                               link
0                      Port Forwarding with iptables         /2018/12/31/Port-Forwarding-with-iptables/
1  Cara download file di google drive dengan comm...  /2018/12/26/Cara-download-file-di-google-drive...
2                Rangkuman Manajemen Perangkat Lunak   /2018/12/20/Rangkuman-Manajemen-Perangkat-Lunak/
3                   Rangkuman manajemen Kepemimpinan      /2018/12/20/Rangkuman-manajemen-Kepemimpinan/
4                                    Kumpulan Materi     /2018/12/18/Kumpulan-Materi-Pemrogaman-Visual/
5                    Hack RDP windows dengan RDPWrap    /2018/12/18/Hack-RDP-windows-dengan-RDPWrapper/
6                            UAS - Keamanan Jaringan                 /2018/12/18/UAS-Keamanan-Jaringan/
7         Cara berkomunikasi pada ssh tanpa password     /2018/12/18/cara-berkomunikasi-tanpa-password/
8                     Sapaan dari yang punya blog :(                /2018/12/18/Binggung-mau-nulis-apa/
9                                   pengenalan-linux                      /2018/09/25/pengenalan-linux/

```

sekian untuk pembahasan web scraping kali ini, semoga bermanfaat. wassalamu'alaikum wr wb