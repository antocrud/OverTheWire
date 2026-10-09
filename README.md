#   Over The Wire

[OverTheWire](https://overthewire.org/wargames/bandit/) is a platform that offers a series of security-oriented wargames designed to develop practical cybersecurity skills through hands-on challenges. The Bandit wargame is aimed at beginners and focuses on Linux fundamentals, command-line usage, file permissions, SSH, text processing, and basic Git operations.

This repository contains my personal notes and step-by-step walkthroughs documenting the process of solving the Bandit challenges, including the commands used and the concepts learned along the way.


##  Bandit Level 0

The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.

```sh
antoc@Lenovo88:~/ctf/overTheWire$ ssh -p 2220 bandit0@bandit.labs.overthewire.org
```
##  Bandit Level 0 → Level 1
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.
```sh
bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme 
Congratulations on your first steps into the bandit game!!
Please make sure you have read the rules at https://overthewire.org/rules/
If you are following a course, workshop, walkthrough or other educational activity,
please inform the instructor about the rules as well and encourage them to
contribute to the OverTheWire community so we can keep these games free!

The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
bandit0@bandit:~$ exit
```

##  Bandit Level 1 → Level 2
The password for the next level is stored in a file called `-` located in the home directory
```sh
bandit1@bandit:~$ cat ./-
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

##  Bandit Level 2 → Level 3
The password for the next level is stored in a file called --spaces in this filename-- located in the home directory
```sh
bandit2@bandit:~$ cat ./--spaces\ in\ this\ filename-- 
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

##  Bandit Level 3 → Level 4
The password for the next level is stored in a hidden file in the inhere directory.
```sh
bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ ls -la
total 12
drwxr-xr-x 2 root    root    4096 Oct 14 09:26 .
drwxr-xr-x 3 root    root    4096 Oct 14 09:26 ..
-rw-r----- 1 bandit4 bandit3   33 Oct 14 09:26 ...Hiding-From-You
bandit3@bandit:~/inhere$ cat ...Hiding-From-You 
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

##  Bandit Level 4 → Level 5
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.
```sh
bandit4@bandit:~$ ls
inhere
bandit4@bandit:~$ cd inhere/
bandit4@bandit:~/inhere$ file ./*
./-file00: data
./-file01: OpenPGP Public Key
./-file02: OpenPGP Public Key
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
bandit4@bandit:~/inhere$ cat ./-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

##  Bandit Level 5 → Level 6
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
-   human-readable
-   1033 bytes in size
-   not executable

```sh
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere02  maybehere04  maybehere06  maybehere08  maybehere10  maybehere12  maybehere14  maybehere16  maybehere18
maybehere01  maybehere03  maybehere05  maybehere07  maybehere09  maybehere11  maybehere13  maybehere15  maybehere17  maybehere19
bandit5@bandit:~/inhere$ find ./* -size 1033c
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

##  Bandit Level 6 → Level 7
The password for the next level is stored somewhere on the server and has all of the following properties:
-   owned by user bandit7
-   owned by group bandit6
-   33 bytes in size
```sh
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
/var/lib/dpkg/info/bandit7.password
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

##  Bandit Level 7 → Level 8
The password for the next level is stored in the file data.txt next to the word millionth
```sh
bandit7@bandit:~$ ls
data.txt
bandit7@bandit:~$ cat data.txt | grep millionth
millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

##  Bandit Level 8 → Level 9
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once
```sh
bandit8@bandit:~$ sort data.txt | uniq -u
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```

##  Bandit Level 9 → Level 10
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.
```sh
bandit9@bandit:~$ strings data.txt | grep "="
========== the
9=H`
[!#=Z
========== password
xWf=
f\Z'========== is
e=i{\#
/1=s
nS=F
M=Sl
=LGT
y =1
========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
'+Y=+
```
##  Bandit Level 10 → Level 11
The password for the next level is stored in the file data.txt, which contains base64 encoded data
```sh
bandit10@bandit:~$ base64 -d data.txt 
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

##  Bandit Level 11 → Level 12
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions
```sh
bandit11@bandit:~$ cat data.txt 
Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4
bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

##  Bandit Level 12 → Level 13
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)
```sh
bandit12@bandit:~$ mktemp -d
/tmp/tmp.UNWWliMtoK
bandit12@bandit:~$ cd /tmp/tmp.UNWWliMtoK
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ cp ~/data.txt .
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ mv data.txt hexdump_data
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ cat hexdump_data | head
"00000000: 1f8b 0808 2e17 ee68 0203 6461 7461 322e  .......h..data2.
00000010: 6269 6e00 0134 02cb fd42 5a68 3931 4159  bin..4...BZh91AY
00000020: 2653 59b6 7680 8b00 001a ffff fadd cfd6  &SY.v...........
00000030: f2e7 f6bb b87f 57ee fff3 b7d7 8bfd fafe  ......W.........
00000040: bffe fdfd d9ef 3dff bfff bdff b001 3aa1  ......=.......:.
00000050: a40d 007a 9901 a000 1a01 a000 1934 7a80  ...z.........4z.
00000060: 6993 469a 6800 0068 1a00 0340 680d 0d00  i.F.h..h...@h...
00000070: 01a6 8794 188d 0c27 a8d3 4608 8006 4d01  .......'..F...M.
00000080: 8800 3268 c8d0 3434 0006 9a19 0f50 3400  ..2h..44.....P4.
00000090: 1840 6403 2064 0034 1934 c468 c862 6868  .@d. d.4.4.h.bhh"
```
```sh
# revert the hexdump to get the actual data
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ xxd -r hexdump_data compressed_data
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ file compressed_data 
compressed_data: gzip compressed data, was "data2.bin", last modified: Tue Oct 14 09:26:06 2025, max compression, from Unix, original size modulo 2^32 564

bandit12@bandit:/tmp/tmp.UNWWliMtoK$ mv compressed_data compressed_data.bz
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ mv compressed_data.bz compressed_data.gz
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ gzip -d compressed_data.gz 
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ ls
compressed_data  hexdump_data
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ file compressed_data 
compressed_data: bzip2 compressed data, block size = 900k

bandit12@bandit:/tmp/tmp.UNWWliMtoK$ mv compressed_data compressed_data.bz2
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ bzip2 -d compressed_data.bz2 
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ file compressed_data 
compressed_data: gzip compressed data, was "data4.bin", last modified: Tue Oct 14 09:26:06 2025, max compression, from Unix, original size modulo 2^32 20480

bandit12@bandit:/tmp/tmp.UNWWliMtoK$ mv compressed_data compressed_data.gz
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ gzip -d compressed_data.gz 
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ file compressed_data 
compressed_data: POSIX tar archive (GNU)

bandit12@bandit:/tmp/tmp.UNWWliMtoK$ mv compressed_data compressed_data.tar
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ tar -xf compressed_data.tar 
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ ls
compressed_data.tar  data5.bin  hexdump_data
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ file data5.bin 
data5.bin: POSIX tar archive (GNU)

bandit12@bandit:/tmp/tmp.UNWWliMtoK$ tar -xf data5.bin
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ ls
compressed_data.tar  data5.bin  data6.bin  hexdump_data
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ file data6.bin 
data6.bin: bzip2 compressed data, block size = 900k

bandit12@bandit:/tmp/tmp.UNWWliMtoK$ bzip2 -d data6.bin
bzip2: Cant guess original name for data6.bin -- using data6.bin.out
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ ls
compressed_data.tar  data5.bin  data6.bin.out  hexdump_data
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ file data6.bin.out 
data6.bin.out: POSIX tar archive (GNU)

bandit12@bandit:/tmp/tmp.UNWWliMtoK$ tar -xf data6.bin.out
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ ls
compressed_data.tar  data5.bin  data6.bin.out  data8.bin  hexdump_data
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ file data8.bin 
data8.bin: gzip compressed data, was "data9.bin", last modified: Tue Oct 14 09:26:06 2025, max compression, from Unix, original size modulo 2^32 49

bandit12@bandit:/tmp/tmp.UNWWliMtoK$ mv data8.bin data8.gz
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ gzip -d data8.gz 
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ ls
compressed_data.tar  data5.bin  data6.bin.out  data8  hexdump_data
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ file data8
data8: ASCII text
bandit12@bandit:/tmp/tmp.UNWWliMtoK$ cat data8
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```

##  Bandit Level 13 → Level 14
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on
```sh
antoc@Lenovo88:~/ctf/overTheWire$ ssh -p 2220 bandit13@bandit.labs.overthewire.org

bandit13@bandit:~$ ls 
sshkey.private

bandit13@bandit:~$ exit

antoc@Lenovo88:~/ctf/overTheWire$ scp -P 2220 bandit13@bandit.labs.overthewire.org:~/sshkey.private .
antoc@Lenovo88:~/ctf/overTheWire$ ls
otw.md sshkey.private

antoc@Lenovo88:~/ctf/overTheWire$ ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0640 for 'sshkey.private' are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
Load key "sshkey.private": bad permissions
# so change the permission
antoc@Lenovo88:~/ctf/overTheWire$ chmod 700 sshkey.private 
antoc@Lenovo88:~/ctf/overTheWire$ ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org
```

##  Bandit Level 14 → Level 15
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.
```sh
bandit14@bandit:~$ cd /etc/bandit_pass/
bandit14@bandit:/etc/bandit_pass$ cat bandit14
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

bandit14@bandit:/etc/bandit_pass$ telnet localhost 30000
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.

MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
Correct!
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

Connection closed by foreign host.
```

##  Bandit Level 15 → Level 16
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.
```sh
bandit15@bandit:~$ cat /etc/bandit_pass/bandit15
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

bandit15@bandit:~$ openssl s_client -connect localhost:30001
CONNECTED(00000003)
Cant use SSL_get_servername
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
...
read R BLOCK

8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
Correct!
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
```

##  Bandit Level 16 → Level 17
The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.
```sh
bandit16@bandit:~$ cat /etc/bandit_pass/bandit16
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

bandit16@bandit:~$ nmap -sV -p 31000-32000 localhost
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-10-21 15:48 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00016s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT      STATE SERVICE     VERSION
31046/tcp open  echo
31518/tcp open  ssl/echo
31691/tcp open  echo
31790/tcp open  ssl/unknown
31960/tcp open  echo
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port31790-TCP:V=7.94SVN%T=SSL%I=7%D=10/21%Time=68F7AB47%P=x86_64-pc-lin
SF:ux-gnu%r(GenericLines,32,"Wrong!\x20Please\x20enter\x20the\x20correct\x
SF:20current\x20password\.\n")%r(GetRequest,32,"Wrong!\x20Please\x20enter\
SF:x20the\x20correct\x20current\x20password\.\n")%r(HTTPOptions,32,"Wrong!
SF:\x20Please\x20enter\x20the\x20correct\x20current\x20password\.\n")%r(RT
SF:SPRequest,32,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x2
SF:0password\.\n")%r(Help,32,"Wrong!\x20Please\x20enter\x20the\x20correct\
SF:x20current\x20password\.\n")%r(FourOhFourRequest,32,"Wrong!\x20Please\x
SF:20enter\x20the\x20correct\x20current\x20password\.\n")%r(LPDString,32,"
SF:Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x20password\.\n"
SF:)%r(SIPOptions,32,"Wrong!\x20Please\x20enter\x20the\x20correct\x20curre
SF:nt\x20password\.\n");

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 145.33 seconds

# seems to be 31790
bandit16@bandit:~$ openssl s_client -connect localhost:31790 -quiet
Cant use SSL_get_servername
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil
verify return:1

kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558Y...euZ/ujbjY
-----END RSA PRIVATE KEY-----

bandit16@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
antoc@Lenovo88:~/ctf/overTheWire$ touch sshkey17.private
antoc@Lenovo88:~/ctf/overTheWire$ nano sshkey17.private     # paste the rsa key
antoc@Lenovo88:~/ctf/overTheWire$ chmod 700 sshkey17.private    # change permissions
```

##  Bandit Level 17 → Level 18
here are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19
```sh
antoc@Lenovo88:~/ctf/overTheWire$ ssh -i sshkey17.private -p 2220 bandit17@bandit.labs.overthewire.org
bandit17@bandit:~$ diff passwords.new passwords.old 
42c42
< x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
---
> pGozC8kOHLkBMOaL0ICPvLV1IjQ5F1VA
```

##  Bandit Level 18 → Level 19
The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified `.bashrc` to log you out when you log in with SSH.

```sh
antoc@Lenovo88:~/ctf/overTheWire$ ssh -p 2220 bandit18@bandit.labs.overthewire.org
...

Enjoy your stay!

Byebye !
Connection to bandit.labs.overthewire.org closed.

# two possible solution
# using scp
antoc@Lenovo88:~/ctf/overTheWire$ scp -P 2220 bandit18@bandit.labs.overthewire.org:~/readme .
antoc@Lenovo88:~/ctf/overTheWire$ cat readme 
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8

# using ssh command directly
antoc@Lenovo88:~/ctf/overTheWire$ ssh -p 2220 bandit18@bandit.labs.overthewire.org ls
...
bandit18@bandit.labs.overthewire.orgs password:  
readme

antoc@Lenovo88:~/ctf/overTheWire$ ssh -p 2220 bandit18@bandit.labs.overthewire.org cat readme
...
bandit18@bandit.labs.overthewire.orgs password: 
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
```

##  Bandit Level 19 → Level 20
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.
```sh
antoc@Lenovo88:~/ctf/overTheWire$ ssh -p 2220 bandit19@bandit.labs.overthewire.org
bandit19@bandit:~$ ls -l
total 16
-rwsr-x--- 1 bandit20 bandit19 14884 Oct 14 09:26 bandit20-do
# the s means that can be executed as if it is executed by bandit20 (the owner)
bandit19@bandit:~$ file bandit20-do 
bandit20-do: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, BuildID[sha1]=38f1351d0068ccbbace0e437f34859de85e63025, for GNU/Linux 3.2.0, not stripped

bandit19@bandit:~$ ./bandit20-do ls 
bandit20-do
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
```

##  Bandit Level 20 → Level 21
There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

NOTE: Try connecting to your own network daemon to see if it works as you think
```sh
antoc@Lenovo88:~/ctf/overTheWire$ ssh -p 2220 bandit20@bandit.labs.overthewire.org
bandit20@bandit:~$ ls -l
total 16
-rwsr-x--- 1 bandit21 bandit20 15608 Oct 14 09:26 suconnect

# we can use nc to create a server listening (-l) on a specific port (-p), using & to execute in background and continue to use this terminal
# we send the previous pwd using echo
bandit20@bandit:~$ echo '4pIjcunZ0fK2vmp3IwfG8Vf7VhxD6pOA' | nc -l -p 8888 &
[1] 47

bandit20@bandit:~$ ./suconnect 8888
Read: 4pIjcunZ0fK2vmp3IwfG8Vf7VhxD6pOA
Password matches, sending next password
bW9kBv5WC3P4yoDyf12LSdGuNz5ka6hY
[1]+  Done                       echo '4pIjcunZ0fK2vmp3IwfG8Vf7VhxD6pOA' | nc -l -p 8888
```

##  Bandit Level 21 → Level 22
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in `/etc/cron.d/` for the configuration and see what command is being executed.
```sh
ssh -p 2220 bandit21@bandit.labs.overthewire.org
bW9kBv5WC3P4yoDyf12LSdGuNz5ka6hY
```
```sh
# moving to the folder
bandit21@bandit:~$ cd /etc/cron.d/
# trying to use cron
bandit21@bandit:/etc/cron.d$ cron
cron: cant open or create /var/run/crond.pid: Permission denied
bandit21@bandit:/etc/cron.d$ cron man
cron: cant open or create /var/run/crond.pid: Permission denied
bandit21@bandit:/etc/cron.d$ man cron
bandit21@bandit:/etc/cron.d$ cron -L 15
cron: cant open or create /var/run/crond.pid: Permission denied

bandit21@bandit:/etc/cron.d$ ls -la
total 56
drwxr-xr-x   2 root root  4096 Sep 27 06:51 .
drwxr-xr-x 128 root root 12288 Sep 27 06:54 ..
-rw-r--r--   1 root root   102 Nov  5  2025 .placeholder
-r--r-----   1 root root    47 Sep 26 21:55 behemoth4_cleanup
-rw-r--r--   1 root root   127 Sep 27 06:51 clean_tmp
-rw-r--r--   1 root root   120 Sep 26 21:54 cronjob_bandit22
-rw-r--r--   1 root root   122 Sep 26 21:54 cronjob_bandit23
-rw-r--r--   1 root root   120 Sep 26 21:54 cronjob_bandit24
-rw-r--r--   1 root root   188 Feb 13  2026 e2scrub_all
-r--r-----   1 root root    48 Sep 26 21:56 leviathan5_cleanup
-rw-------   1 root root   138 Sep 26 21:56 manpage3_resetpw_job
-rwx------   1 root root    52 Sep 26 21:58 otw-tmp-dir

# let's see in the files
bandit21@bandit:/etc/cron.d$ cat bahemoth4_cleanup
cat: bahemoth4_cleanup: No such file or directory
bandit21@bandit:/etc/cron.d$ cat cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
bandit21@bandit:/etc/cron.d$ cat cronjob_bandit23
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
bandit21@bandit:/etc/cron.d$ cat cronjob_bandit24
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null

# lets try again cron
bandit21@bandit:/etc/cron.d$ cron -f
cron: cant open or create /var/run/crond.pid: Permission denied

bandit21@bandit:/etc/cron.d$ cat clean_tmp
*/30 * * * * root find /tmp -amin +60 -type f,l -delete &> /dev/null && find /tmp -amin +5 -type d -empty -delete &> /dev/null
bandit21@bandit:/etc/cron.d$ cat e2scrub_all 
30 3 * * 0 root test -e /run/systemd/system || SERVICE_MODE=1 /usr/libexec/e2fsprogs/e2scrub_all_cron
10 3 * * * root test -e /run/systemd/system || SERVICE_MODE=1 /sbin/e2scrub_all -A -r
bandit21@bandit:/etc/cron.d$ cat manpage3_resetpw_job 
cat: manpage3_resetpw_job: Permission denied
bandit21@bandit:/etc/cron.d$ cat leviathan5_cleanup 
cat: leviathan5_cleanup: Permission denied

# maybe it is in those files, probably the 22
bandit21@bandit:/etc/cron.d$ cat cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
# mmm lets look at that sh file
bandit21@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
# seems god, lets see in that file
bandit21@bandit:/etc/cron.d$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
RYVux2rHEm9tiXHmLFzuR7Vhx6AZQMEz
# lets go
```

##  Bandit Level 22 → Level 23
A program is running automatically at regular intervals from cron, the time-based job scheduler. 

Look in `/etc/cron.d/` for the configuration and see what command is being executed.

NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.
```sh
ssh -p 2220 bandit22@bandit.labs.overthewire.org
RYVux2rHEm9tiXHmLFzuR7Vhx6AZQMEz
```
```sh
bandit22@bandit:~$ cd /etc/cron.d
bandit22@bandit:/etc/cron.d$ ls -la
total 56
drwxr-xr-x   2 root root  4096 Sep 27 06:51 .
drwxr-xr-x 128 root root 12288 Sep 27 06:54 ..
-rw-r--r--   1 root root   102 Nov  5  2025 .placeholder
-r--r-----   1 root root    47 Sep 26 21:55 behemoth4_cleanup
-rw-r--r--   1 root root   127 Sep 27 06:51 clean_tmp
-rw-r--r--   1 root root   120 Sep 26 21:54 cronjob_bandit22
-rw-r--r--   1 root root   122 Sep 26 21:54 cronjob_bandit23
-rw-r--r--   1 root root   120 Sep 26 21:54 cronjob_bandit24
-rw-r--r--   1 root root   188 Feb 13  2026 e2scrub_all
-r--r-----   1 root root    48 Sep 26 21:56 leviathan5_cleanup
-rw-------   1 root root   138 Sep 26 21:56 manpage3_resetpw_job
-rwx------   1 root root    52 Sep 26 21:58 otw-tmp-dir
bandit22@bandit:/etc/cron.d$ cat cronjob_bandit23
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
bandit22@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit23.sh
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
```
```sh
bandit22@bandit:/etc/cron.d$ whoami
bandit22
bandit22@bandit:/etc/cron.d$ echo I am user bandit22 | md5sum | cut -d ' ' -f 1
8169b67bd894ddbb4412f91573b38db3

bandit22@bandit:/etc/cron.d$ cat /tmp/8169b67bd894ddbb4412f91573b38db3
RYVux2rHEm9tiXHmLFzuR7Vhx6AZQMEz
# we are good right? well the pwd does not work

# mmm
# but the file is executed by bandit23
bandit22@bandit:/etc/cron.d$ echo I am user bandit23 | md5sum | cut -d ' ' -f 1
8ca319486bfbbc3663ea0fbe81326349
bandit22@bandit:/etc/cron.d$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349
gKXDTAXnIz3OBxiPjRZ2uqutUlPZrBsw
# here we go
```

##  Bandit Level 23 → Level 24
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…
```sh
ssh -p 2220 bandit23@bandit.labs.overthewire.org
gKXDTAXnIz3OBxiPjRZ2uqutUlPZrBsw
```
```sh
bandit23@bandit:~$ cd /etc/cron.d
bandit23@bandit:/etc/cron.d$ ls
behemoth4_cleanup  cronjob_bandit22  cronjob_bandit24  leviathan5_cleanup    otw-tmp-dir
clean_tmp          cronjob_bandit23  e2scrub_all       manpage3_resetpw_job
bandit23@bandit:/etc/cron.d$ cat cronjob_bandit24 
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
bandit23@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

shopt -s nullglob

myname=$(whoami)

cd /var/spool/"$myname"/foo || exit 
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." ] && [ "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" "./$i")"
        if [ "${owner}" = "bandit23" ] && [ -f "$i" ]; then
            timeout -s 9 60 "./$i"
        fi
        rm -rf "./$i"
    fi
done
```
we can see that the cron is executing all the files in the `/var/spool/bandit24/foo` folder, by bandit24, but can also execute files created by bandit23: `if [ "${owner}" = "bandit23" ] && [ -f "$i" ]; then`.

So we need to create a file there, that print the pwd of b24, and we can do it, since is b24 that is executing the file, so have access to its pwd
```sh
bandit23@bandit:/var/spool/bandit24/foo$ ls -ld .
drwxrwx-wx 6 root bandit24 4096 Oct  9 08:51 .
# as we can see, we cannot list the folder, but we can write in it

# lets create another folder, to create the script
bandit23@bandit:/var/spool/bandit24/foo$ mkdir /tmp/124
bandit23@bandit:/var/spool/bandit24/foo$ cd /tmp/124
bandit23@bandit:/tmp/124$ nano bandit23luca.sh
#!/bin/bash
myname=$(whoami)
cat /etc/bandit_pass/$myname 

mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget

#
chmod +x bandit23luca.sh
bandit23@bandit:/tmp/124$ ls -la
total 4
drwxrwxr-x   2 bandit23 bandit23   60 Oct  9 08:56 .
drwxrwx-wt 112 root     root     2700 Oct  9 08:57 ..
-rwxrwxr-x   1 bandit23 bandit23  260 Oct  9 08:56 bandit23luca.sh

# now we can copy it in that folder
bandit23@bandit:/tmp/124$ cp bandit23luca.sh /var/spool/bandit24/foo
# ok now, as the previous level, we can print the pwd
bandit23@bandit:/tmp/124$ echo I am user bandit24 | md5sum | cut -d ' ' -f 1
ee4ee1703b083edac9f8183e4ae70293
bandit23@bandit:/tmp/124$ cat /tmp/ee4ee1703b083edac9f8183e4ae70293
hVQMk3lJNsmQ7VF3ubyrNNBom7BOgVXv
```

##  Bandit Level 24 → Level 25
A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.
You do not need to create new connections each time
```sh
ssh -o ServerAliveInterval=60 -o ServerAliveCountMax=3 -p 2220 bandit24@bandit.labs.overthewire.org
hVQMk3lJNsmQ7VF3ubyrNNBom7BOgVXv
```
we need to create a script that tries every pin possibility
```sh
bandit24@bandit:~$ nc localhost 30002
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
```

we can create a bash file to try all possibilities
```sh
!/bin/bash

password24=hVQMk3lJNsmQ7VF3ubyrNNBom7BOgVXv

for i in {0..10}; do
    msg="${password24} ${i}"
    echo "Tentativo numero $i: invio ${msg}"
    echo "$msg" | nc -q 1 localhost 30002
done

# now the one for all attempts
for i in {0000..9999}; do
    msg="${password24} ${i}"
    echo "$msg" | nc -q 0 localhost 30002
done
```
was not working so, ... other option

```sh
bandit24@bandit:/tmp/12345$ nano bf.sh
#!/bin/bash

for i in {0000..9999} 
do
        echo hVQMk3lJNsmQ7VF3ubyrNNBom7BOgVXv $i >> possibilities.txt
done

cat possibilities.txt | nc localhost 30002 > result.txt


#
bandit24@bandit:/tmp/12345$ chmod +x bf.sh
bandit24@bandit:/tmp/12345$ ./bf.sh
bandit24@bandit:/tmp/12345$ ls -l
total 564
-rwx--x--x 1 bandit24 bandit24    164 Oct  9 09:39 bf.sh
-rw-rw-r-- 1 bandit24 bandit24 380000 Oct  9 09:39 possibilities.txt
-rw-rw-r-- 1 bandit24 bandit24 187034 Oct  9 09:39 result.txt
-rwxrwxr-x 1 bandit24 bandit24    326 Oct  9 09:35 script24.sh

bandit24@bandit:/tmp/12345$ sort result.txt | grep -v "Wrong!"
Correct!
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
The password of user bandit25 is SoHfqMOEqIX2IYKVciZxvgpR9a2Djx4P
```

##  Bandit Level 25 → Level 26
Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

NOTE: if you’re a Windows user and typically use Powershell to ssh into bandit: Powershell is known to cause issues with the intended solution to this level. You should use command prompt instead.
```sh
ssh -o ServerAliveInterval=60 -o ServerAliveCountMax=3 -p 2220 bandit25@bandit.labs.overthewire.org
SoHfqMOEqIX2IYKVciZxvgpR9a2Djx4P
```
```sh
bandit25@bandit:~$ ls -la
total 40
drwxr-xr-x   2 root     root     4096 Sep 26 21:54 .
drwxr-xr-x 150 root     root     4096 Sep 26 21:58 ..
-rw-r-----   1 bandit25 bandit25   33 Sep 26 21:54 .bandit24.password
-rw-r-----   1 bandit25 bandit25  151 Sep 26 21:54 .banner
-rw-r--r--   1 root     root      220 Feb 13  2026 .bash_logout
-rw-r--r--   1 root     root     3851 Sep 26 21:38 .bashrc
-rw-r-----   1 bandit25 bandit25   66 Sep 26 21:54 .flag
-rw-r-----   1 bandit25 bandit25    4 Sep 26 21:54 .pin
-rw-r--r--   1 root     root      807 Feb 13  2026 .profile
-r--------   1 bandit25 bandit25 2602 Sep 26 21:54 bandit26.sshkey

# saved the ssh key, trying to connect to b26, but the connection is closed as soon as we enter.
```
```sh
bandit25@bandit:~$ cat /etc/passwd | grep bandit26  # to see what kind of shell
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext

bandit25@bandit:~$ cat /usr/bin/showtext
#!/bin/sh

export TERM=linux

exec more ~/text.txt
exit 0
bandit25@bandit:~$ more ~/text.txt
more: cannot open /home/bandit25/text.txt: No such file or directory
```
tring again to log in with ssh and the sk. reducing the height of the window (showing only few rows) will keep the terminal open

now pressing v we can use vim, to set the shell
```sh
:set shell=/bin/bash
:shell

# now we spawned a shell on that terminal
bandit26@bandit:~$ ls -l
total 20
-rwsr-x--- 1 bandit27 bandit26 14880 Sep 26 21:54 bandit27-do
-rw-r----- 1 bandit26 bandit26   258 Sep 26 21:54 text.txt

# now retrieving the pwd
bandit26@bandit:~$ cat /etc/bandit_pass/bandit26
jHdv2ELQhT22BkprMNDjybZDAkw1zeBJ
```

##  Bandit Level 26 → Level 27
Good job getting a shell! Now hurry and grab the password for bandit27!

We are still on the shell spawned on the last level
```sh
bandit26@bandit:~$ ls -l
total 20
-rwsr-x--- 1 bandit27 bandit26 14880 Sep 26 21:54 bandit27-do
-rw-r----- 1 bandit26 bandit26   258 Sep 26 21:54 text.txt
bandit26@bandit:~$ cat bandit27-do
ELFp4�5LL ,�xx ��$$! �/
....
�/��/��/�0�00&@0p    2��4

bandit26@bandit:~$ file bandit27-do
bandit27-do: setuid ELF 32-bit LSB executable, Intel i386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, BuildID[sha1]=55720343cddb2e256343bc366b061e1a71764f51, for GNU/Linux 3.2.0, not stripped
bandit26@bandit:~$ ./bandit27-do
Run a command as another user.
  Example: ./bandit27-do id
bandit26@bandit:~$ id
uid=11026(bandit26) gid=11026(bandit26) groups=11026(bandit26)
bandit26@bandit:~$ ./bandit27-do 11027
env: '11027': Permission denied
bandit26@bandit:~$ ./bandit27-do whoami
bandit27
# so it is executed as i was b27
bandit26@bandit:~$ ./bandit27-do cat /etc/bandit_pass/bandit27
STJLJBRRphMxKB392CT4iOr5CbzPU9ER
```

##  Bandit Level 27 → Level 28
There is a git repository at ssh://bandit27-git@bandit.labs.overthewire.org/home/bandit27-git/repo via the port 2220. The password for the user bandit27-git is the same as for the user bandit27.

From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level. This needs git installed locally on your machine.
```sh
ssh -o ServerAliveInterval=60 -o ServerAliveCountMax=3 -p 2220 bandit27@bandit.labs.overthewire.org
STJLJBRRphMxKB392CT4iOr5CbzPU9ER
```
```sh
antoc@Lenovo88:~/ctf/overTheWire$ GIT_SSH_COMMAND="ssh -p 2220" git clone ssh://bandit27-git@bandit.labs.overthewire.org/home/bandit27-git/repo
Cloning into 'repo'...
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-0
bandit27-git@bandit.labs.overthewire.org password: 
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
Receiving objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
antoc@Lenovo88:~/ctf/overTheWire$ ls -l
total 76
-rw-r--r-- 1 antoc antoc 18429 Oct  9 12:38 image.png
-rw-r--r-- 1 antoc antoc 34594 Oct  9 12:56 otw.md
-rw-r----- 1 antoc antoc    33 Oct  8 12:50 readme
drwxr-xr-x 3 antoc antoc  4096 Oct  9 12:56 repo
-rwx------ 1 antoc antoc  2602 Oct  8 12:37 sshkey.private
-rw------- 1 antoc antoc  2602 Oct  8 12:48 sshkey17.private
-rw------- 1 antoc antoc  2602 Oct  9 12:14 sshkey26.private
antoc@Lenovo88:~/ctf/overTheWire$ cd repo/
antoc@Lenovo88:~/ctf/overTheWire/repo$ ls -l
total 4
-rw-r--r-- 1 antoc antoc 68 Oct  9 12:56 README

antoc@Lenovo88:~/ctf/overTheWire/repo$ cat README 
The password to the next level is: y8Yd2ssKcpHpud7UvOSOxwamRMzIGIeQ
```

##  Bandit Level 28 → Level 29
There is a git repository at ssh://bandit28-git@bandit.labs.overthewire.org/home/bandit28-git/repo via the port 2220. The password for the user bandit28-git is the same as for the user bandit28.

From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level. This needs git installed locally on your machine.
```sh
GIT_SSH_COMMAND="ssh -p 2220" git clone ssh://bandit28-git@bandit.labs.overthewire.org/home/bandit28-git/repo repo28

antoc@Lenovo88:~/ctf/overTheWire/repo28$ ls -la
total 16
drwxr-xr-x 3 antoc antoc 4096 Oct  9 12:59 .
drwxr-xr-x 4 antoc antoc 4096 Oct  9 12:59 ..
drwxr-xr-x 8 antoc antoc 4096 Oct  9 12:59 .git
-rw-r--r-- 1 antoc antoc  111 Oct  9 12:59 README.md

antoc@Lenovo88:~/ctf/overTheWire/repo28$ cat README.md
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: xxxxxxxxxx



antoc@Lenovo88:~/ctf/overTheWire/repo28$ git log
commit de09b8205d8d115e2749670df21bf1882bc98e34 (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Sat Sep 26 21:54:43 2026 +0000

    fix info leak

commit ad8a5f812f24e793d2657f926f503a2fd1c5e256
Author: Morla Porla <morla@overthewire.org>
Date:   Sat Sep 26 21:54:43 2026 +0000

    add missing data

commit e4337f154bd5cc106d3d047fc72f90b187ffcfab
Author: Ben Dover <noone@overthewire.org>
Date:   Sat Sep 26 21:54:43 2026 +0000

    initial commit of README.md
antoc@Lenovo88:~/ctf/overTheWire/repo28$ git log -p -- README.md
commit de09b8205d8d115e2749670df21bf1882bc98e34 (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Sat Sep 26 21:54:43 2026 +0000

    fix info leak

diff --git a/README.md b/README.md
index 42331d9..5c6457b 100644
--- a/README.md
+++ b/README.md
@@ -4,5 +4,5 @@ Some notes for level29 of bandit.
 ## credentials
 
 - username: bandit29
-- password: Em7eGtqaMySwNFjCpwzzHhLhospOcdt0
+- password: xxxxxxxxxx
 

commit ad8a5f812f24e793d2657f926f503a2fd1c5e256
Author: Morla Porla <morla@overthewire.org>
Date:   Sat Sep 26 21:54:43 2026 +0000

    add missing data

diff --git a/README.md b/README.md
:
commit de09b8205d8d115e2749670df21bf1882bc98e34 (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Sat Sep 26 21:54:43 2026 +0000

    fix info leak

diff --git a/README.md b/README.md
index 42331d9..5c6457b 100644
--- a/README.md
+++ b/README.md
@@ -4,5 +4,5 @@ Some notes for level29 of bandit.
 ## credentials
 
 - username: bandit29
-- password: Em7eGtqaMySwNFjCpwzzHhLhospOcdt0
+- password: xxxxxxxxxx
 

commit ad8a5f812f24e793d2657f926f503a2fd1c5e256
Author: Morla Porla <morla@overthewire.org>
Date:   Sat Sep 26 21:54:43 2026 +0000

    add missing data

diff --git a/README.md b/README.md
```

##  Bandit Level 29 → Level 30
There is a git repository at ssh://bandit29-git@bandit.labs.overthewire.org/home/bandit29-git/repo via the port 2220. The password for the user bandit29-git is the same as for the user bandit29.

From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level. This needs git installed locally on your machine.
```sh
antoc@Lenovo88:~/ctf/overTheWire$ GIT_SSH_COMMAND="ssh -p 2220" git clone ssh://bandit29-git@bandit.labs.overthewire.org/home/bandit29-git/repo repo29

antoc@Lenovo88:~/ctf/overTheWire$ cd repo29/
antoc@Lenovo88:~/ctf/overTheWire/repo29$ ls -l
total 4
-rw-r--r-- 1 antoc antoc 131 Oct  9 13:07 README.md
antoc@Lenovo88:~/ctf/overTheWire/repo29$ cat README.md 
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>

# no prior commit related to the pwd
# lets look in other branches
antoc@Lenovo88:~/ctf/overTheWire/repo29$ git branch -a
* master
  master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  remotes/origin/sploits-dev

antoc@Lenovo88:~/ctf/overTheWire/repo29$ git switch dev
Switched to branch 'dev'
Your branch is up to date with 'origin/dev'.
antoc@Lenovo88:~/ctf/overTheWire/repo29$ git log -p -- README.md
commit a6fec80fb492ec1c7502098f37fc4664d67db2d9 (HEAD -> dev, origin/dev)
Author: Morla Porla <morla@overthewire.org>
Date:   Sat Sep 26 21:54:45 2026 +0000

    add data needed for development

diff --git a/README.md b/README.md
index 1af21d3..d395d04 100644
--- a/README.md
+++ b/README.md
@@ -4,5 +4,5 @@ Some notes for bandit30 of bandit.
 ## credentials
 
 - username: bandit30
-- password: <no passwords in production!>
+- password: jq9Dfg2rXsfYsWMgFuKlXhphjdH7USgX
 

commit 5a4df04dc6b1dcee6f1bf558b8e8416dc75e2599 (origin/master, origin/HEAD, master)
Author: Ben Dover <noone@overthewire.org>
Date:   Sat Sep 26 21:54:45 2026 +0000

    fix username

diff --git a/README.md b/README.md
```

##  Bandit Level 30 → Level 31
There is a git repository at ssh://bandit30-git@bandit.labs.overthewire.org/home/bandit30-git/repo via the port 2220. The password for the user bandit30-git is the same as for the user bandit30.

From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level. This needs git installed locally on your machine.
```sh
GIT_SSH_COMMAND="ssh -p 2220" git clone ssh://bandit30-git@bandit.labs.overthewire.org/h
ome/bandit30-git/repo repo30
antoc@Lenovo88:~/ctf/overTheWire$ cd repo30/
antoc@Lenovo88:~/ctf/overTheWire/repo30$ ls -la
total 16
drwxr-xr-x 3 antoc antoc 4096 Oct  9 13:20 .
drwxr-xr-x 6 antoc antoc 4096 Oct  9 13:20 ..
drwxr-xr-x 8 antoc antoc 4096 Oct  9 13:20 .git
-rw-r--r-- 1 antoc antoc   30 Oct  9 13:20 README.md
antoc@Lenovo88:~/ctf/overTheWire/repo30$ cat README.md 
just an epmty file... muahaha

# no previous commit or branches
# lets search if there are any tags
antoc@Lenovo88:~/ctf/overTheWire/repo30$ git tag
secret
antoc@Lenovo88:~/ctf/overTheWire/repo30$ git show secret 
82NkymblpGBYmIXG6ZQ8YldBYstHpfUf
```

##  Bandit Level 31 → Level 32
There is a git repository at ssh://bandit31-git@bandit.labs.overthewire.org/home/bandit31-git/repo via the port 2220. The password for the user bandit31-git is the same as for the user bandit31.

From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level. This needs git installed locally on your machine.
```sh
GIT_SSH_COMMAND="ssh -p 2220" git clone ssh://bandit31-git@bandit.labs.overthewire.org/h
ome/bandit31-git/repo repo31
antoc@Lenovo88:~/ctf/overTheWire$ cd repo31/
antoc@Lenovo88:~/ctf/overTheWire/repo31$ ls -la
total 20
drwxr-xr-x 3 antoc antoc 4096 Oct  9 13:25 .
drwxr-xr-x 7 antoc antoc 4096 Oct  9 13:25 ..
drwxr-xr-x 8 antoc antoc 4096 Oct  9 13:25 .git
-rw-r--r-- 1 antoc antoc    6 Oct  9 13:25 .gitignore
-rw-r--r-- 1 antoc antoc  147 Oct  9 13:25 README.md
antoc@Lenovo88:~/ctf/overTheWire/repo31$ cat .gitignore
*.txt
antoc@Lenovo88:~/ctf/overTheWire/repo31$ cat README.md 
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master

# lets change the gitignore
antoc@Lenovo88:~/ctf/overTheWire/repo31$ cat .gitignore
# *.txt

antoc@Lenovo88:~/ctf/overTheWire/repo31$ echo "May I come in?" > key.txt
antoc@Lenovo88:~/ctf/overTheWire/repo31$ git add -f key.txt 
antoc@Lenovo88:~/ctf/overTheWire/repo31$ git commit -m "Add key.txt"
[master a7cde60] Add key.txt
 1 file changed, 1 insertion(+)
 create mode 100644 key.txt
antoc@Lenovo88:~/ctf/overTheWire/repo31$ git branch
* master
antoc@Lenovo88:~/ctf/overTheWire/repo31$ git push origin master

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

!!! You are trying to log into this SSH server on port 22, which is not intended.
!!! If you are trying to log in to an OverTheWire game, use the port mentioned in
!!! the "SSH Information" on that games webpage (in the top left corner).

bandit31-git@bandit.labs.overthewire.org: Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
antoc@Lenovo88:~/ctf/overTheWire/repo31$ GIT_SSH_COMMAND="ssh -p 2220" git push origin master
backend: gibson-0
bandit31-git@bandit.labs.overthewire.orgs password: 
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 16 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 333 bytes | 333.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote: ### Attempting to validate files... ####
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote: 
remote: Well done! Here is the password for the next level:
remote: pWuj5jBQ6IgV0NXwiH6g1pXRF8S1YvbT 
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote: 
To ssh://bandit.labs.overthewire.org/home/bandit31-git/repo
 ! [remote rejected] master -> master (pre-receive hook declined)
error: failed to push some refs to 'ssh://bandit.labs.overthewire.org/home/bandit31-git/repo'
```

##  Bandit Level 32 → Level 33
After all this git stuff, it’s time for another escape. Good luck!

```sh
antoc@Lenovo88:~/ctf/overTheWire$ ssh -o ServerAliveInterval=60 -o ServerAliveCountMax=3 -p 2220 bandit32@bandit.labs.overthewire.org
pWuj5jBQ6IgV0NXwiH6g1pXRF8S1YvbT


WELCOME TO THE UPPERCASE SHELL
>> ls
sh: 1: LS: Permission denied

# everything seems to be upcase
# nothin usual work, but there is the variable $0 which is a variable with a reference to the shell
antoc@Lenovo88:~/ctf/overTheWire$ echo $0
-bash

>> $0
$ ls -la
total 36
drwxr-xr-x   2 root     root      4096 Sep 26 21:54 .
drwxr-xr-x 150 root     root      4096 Sep 26 21:58 ..
-rw-r--r--   1 root     root       220 Feb 13  2026 .bash_logout
-rw-r--r--   1 root     root      3851 Sep 26 21:38 .bashrc
-rw-r--r--   1 root     root       807 Feb 13  2026 .profile
-rwsr-x---   1 bandit33 bandit32 15136 Sep 26 21:54 uppershell
$ whoami
bandit33
$ cat /etc/bandit_pass/bandit33
u4P2CyPOwPGLe94RdD9Uo2FxFwvnFswM
```

##  Bandit Level 33 → Level 34

```sh
antoc@Lenovo88:~/ctf/overTheWire$ ssh -o ServerAliveInterval=60 -o ServerAliveCountMax=3 -p 2220 bandit33@bandit.labs.overthewire.org
u4P2CyPOwPGLe94RdD9Uo2FxFwvnFswM


bandit33@bandit:~$ ls
README.txt
bandit33@bandit:~$ cat README.txt 
Congratulations on solving the last level of this game!

At this moment, there are no more levels to play in this game. However, we are constantly working
on new levels and will most likely expand this game with more levels soon.
Keep an eye out for an announcement on our usual communication channels!
In the meantime, you could play some of our other wargames.

If you have an idea for an awesome new level, please let us know!
```
