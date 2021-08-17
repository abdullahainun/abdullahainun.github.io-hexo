title: Cara download file di google drive dengan command line di linux
author: Ainun Abdullah
tags: []
categories: 
	- Infrastructure
date: 2018-12-26 17:40:00
---
Hello guys, Assalamulaikum wr wb. gimana kabar kalian hari ini.  Tentunya senang sekali yaaa. karena masih bisa mentengin blog ini... 

Pada kesempatan kali ini, aku pengen berbagi tips atau tutorial agar bisa download file di google drive. caranya mudah banget, yaitu dengan menggunakan tools yang aku temukan di github. berikut linknya.  https://github.com/prasmussen/gdrive.
<!--more-->
untuk lebih jelasnya berikut langkah - langkahnya

1. Download the binary. Choose the one that fits your architecture, for example gdrive-linux-x64. 

2. Copy it to your path.
```
sudo cp gdrive-linux-x64 /usr/local/bin/gdrive;
sudo chmod a+x /usr/local/bin/gdrive;
```

	setelah itu, jalankan ``gdrive download id-url``