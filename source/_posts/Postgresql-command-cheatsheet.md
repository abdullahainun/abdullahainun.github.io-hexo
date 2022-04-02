title: PostgreSQL command cheatsheet
author: Ainun Abdullah
tags:
  - cheatsheet
categories:
  - Infrastructure
date: 2021-08-17 07:00:00
---
This's postgresql notes command
## Basic
```bash
#create new user and database
sudo -u postgres psql
postgres=# create database mydb;
postgres=# create user myuser with encrypted password 'mypass';
postgres=# grant all privileges on database mydb to myuser;

#or with this

$ sudo -u postgres psql
$ sudo -u postgres createuser <username>
$ sudo -u postgres createdb <dbname>
$ sudo -u postgres psql
psql=# alter user <username> with encrypted password '<password>';
psql=# grant all privileges on database <dbname> to <username> ;

# psql version
CREATE DATABASE yourdbname;
CREATE USER youruser WITH ENCRYPTED PASSWORD 'yourpass';
GRANT ALL PRIVILEGES ON DATABASE yourdbname TO youruser;
```
<!--more-->