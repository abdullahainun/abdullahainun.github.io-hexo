title: Linux command cheatsheet
author: Ainun Abdullah
tags:
  - cheatsheet
categories:
  - Infrastructure
date: 2021-08-17 07:00:00
---
This's linux notes command
## Basic
```bash
#change directory
cd
#list of directory
ls
#print working directory
pwd
#show help each command
<command> --help
man <command>
```
<!--more-->
## Spesial Needs
```bash
#kill process by port
sudo kill -9 $(sudo lsof -t -i:4000)
```

## other