title: Cara berkomunikasi pada ssh tanpa password
author: Ainun Abdullah
tags:
  - ssh-key-pair
  - ssh
  - linux-public-key
  - ssh-keygen
  - remote-tanpa-pasword
categories:
  - Infrastructure
date: 2018-12-18 18:19:00
---
Apa itu ssh ?

Menurut wikipedia :

"Secure Shell (SSH) is a cryptographic network protocol for operating network services securely over an unsecured network." 

Jadi kalo saya terjemahkan secara bebas ssh Secure Shell (SSH) adalah protokol jaringan kriptografi untuk mengoperasikan layanan jaringan secara aman melalui jaringan yang tidak aman 
atau kalo temen2 yang sudah biasa di dunia IT biasanya digunakan untuk remote server yang berbasis linux.

Biasanya kalo kita ingin akses linux via ssh. pasti menggunakan password atau certificate key. nah kali ini saya ingin berbagi gimana caranya akses server tanpa menggunakan 2 hal tadi. yang mana cara ini biasa digunakan bila agan2 ingin menggunakan ssh untuk mengirimkan perintah tertentu. langsung saja. silahkan ikuti langkah2 berikut :

1. generate ssh public key pada komputer anda

  ```
      ssh-keygen -b 4096
  ```
  untuk mengenerate public key, kita dapat menggunakan ssh-keygen. dengan menggunakan perintah seperti di atas. setelah itu tekan enter maka akan keluar console dialog seperti di bawah ini. silahkan kosongi dan tekan enter saja. sampai proses selesai
  ```
  	Generating public/private rsa key pair.
      Enter file in which to save the key (/home/user/.ssh/id_rsa):
      Enter passphrase (empty for no passphrase):
      Enter same passphrase again:
      Your identification has been saved in /home/user/.ssh/id_rsa.
      Your public key has been saved in /home/user/.ssh/id_rsa.pub.
      The key fingerprint is:
      f6:61:a8:27:35:cf:4c:6d:13:22:70:cf:4c:c8:a0:23 user@linode
  ```
2. Upload public key kita ke server

	Masuk sebagai user yang ingin menggunakan key pair
```
   ssh user@example.com			
```
buat `.ssh` dan file `authorized_keys` untuk menyimpan key kita
```
	mkdir ~/.ssh && touch ~/.ssh/authorized_keys
	chmod 700 ~/.ssh && chmod 600 ~/.ssh/authorized_keys
```
 kemudian pada mesin local kita, gunakan `scp` untuk mengcopy file public key di local ke server
 ```
 	scp ~/.ssh/id_rsa.pub 	 example_user@203.0.113.10:~/.ssh/authorized_keys
 ```

3. waktunya pengecekan
silahkan ssh server anda dengan perintah berikut dan lihat hasilnya... 
```
ssh user@example.com
```