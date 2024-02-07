# banditdoc
This repository contains writeup for helping in solving bandits- by Sapthami

## Level 0
`ssh` is used for remote login into a server. It can login into different port numbers deployed on a server and it will act as a client to that server.  
`ls` shows the list of available files and directories.  
`file <filename>` shows the type of file  
`cat <filename>` shows the content of the file  
### Commands: 
````
ssh bandit0@bandit.labs.overthewire.org -p 2220  
ls  
cat readme  
exit
````
password for level 1:  
```
NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
```
## Level 1
The given filename is '-', which generally represents an attribute  
To specify that this is a filename, we put ./(dot slash) before the filename 
### Commands: 
```` 
ssh bandit1@bandit.labs.overthewire.org -p 2220  
ls  
cat ./-
exit
````
password for level 2:  
````
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
````
``ping -c 5 1.1.1.1`` is the command to check internet connection. On a properly functioning network you should see 0% packet loss and your average ping time should be below 500ms.  
## Level 2  
The given filename is 'spaces in this filename', which contains spaces in between.  To prevent it from being read as separate filenames, single quotes or double quotes are used.  
### Commands:  
````
ssh bandit2@bandit.labs.overthewire.org -p 2220
ls
cat 'spaces in this filename'
exit
````
password for level 3:  
````
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
````
## Level 3
The given filename '.hidden' is a hidden file in the directory 'inhere'.  To access hidden files, we use the `ls -a` command after entering the directory using `cd <directoryname>` command.  
### Commands:  
````
ssh bandit3@bandit.labs.overthewire.org -p 2220
ls
cd inhere
ls -a
cat .hidden
exit
````
password for level 4:  
````
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
````
## Level 4
`reset` command is used to clear the previous outputs.  
The required filename is the only human-readable file in the 'inhere' directory.  
We find the filetype of all the files in the directory and read data of the ASCII text file only.  
Since the filenames start with hyphen, we use dot slash before referring to them.  
Only -file07 is an ASCII text.  
### Commands: 
````
ssh bandit4@bandit.labs.overthewire.org -p 2220
ls
cd inhere
file ./*
cat ./-file07
exit
````
password for level 5:
````
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
````
## Level 5
The required file is under the 'inhere' directory and is human-readable, 1033 bytes in size and not executable.  
`find -attribute` command is used to filter the resulting files.   
The attribute `! -executable` ensures only non executable files are displayed and `-size 1033c` gives only files of size 1033 bytes.   
`file <filename>` gives the file type, out of which we consider only the ASCII text file.  
### Commands:
````
ssh bandit5@bandit.labs.overthewire.org -p 2220
ls
cd inhere
ls -a
find ! -executable -size 1033c
file ./maybehere07/.file2
cat ./maybehere07/.file2
exit
````
password for level 6: 
````
P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
````
## Level 6
The required file is somewhere in the server and owned by user bandit7, group bandit6 and is 33 bytes in size.  
Using `find -attribute` command, we find the file.  
Inorder to hide the 'permission denied' error messages that are displayed for files we do not have access to, we can append `2>/dev/null`.  
### Commands:
```
ssh bandit6@bandit.labs.overthewire.org -p 2220
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password
exit
```
password for level 7:
```
z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
```
## Level 7
Password is next to the word "millionth" in the file data.txt.  
`grep "word" filename` searches for PATTERNS in each FILE. PATTERNS is one or more patterns separated by newline characters, and grep prints each line that matches a pattern.
### Commands:
```
ssh bandit7@bandit.labs.overthewire.org -p 2220
ls
grep "millionth" data.txt
exit
```
password for level 8:
```
TESKZC0XvTetK0S9xNwm25STk5iWrBvP
```
## Level 8
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.  
`sort <filename>` sorts lines of the text file.  
`uniq -u` filters adjacent duplicate lines from the file and prints only the unique lines.  
### Commands:
```
ssh bandit8@bandit.labs.overthewire.org -p 2220
ls
sort data.txt | uniq -u
exit
```
password for level 9:
```
EN632PlfYiZbn3PhVK3XOGSlNInNE00t
```
## Level 9
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.  
`strings <filename>` command shows all the printable characters in the file.  
`grep "pattern"` prints each line that matches the pattern.  
### Commands: 
```
ssh bandit9@bandit.labs.overthewire.org -p 2220
ls
strings data.txt|grep ===
exit
```
password for level 10: 
```
G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
```
## Level 10
The password for the next level is stored in the file data.txt, which contains base64 encoded data.  
`base64 -d` decodes the data in the file
### Commands: 
```
ssh bandit10@bandit.labs.overthewire.org -p 2220
ls
cat data.txt|base64 -d
exit
```
password for level 11:
```
6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
```
## Level 11
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions
`tr` command translates characters. It takes two sets as inputs, plus an input stream.  
It then takes and looks up each character in the input stream using the first set, and replaces it with the character in the second set at the same position.
### Commands:
```
ssh bandit11@bandit.labs.overthewire.org -p 2220
ls
cat data.txt | tr '[A-Za-z]' '[N-ZA-Mn-za-m]'
exit
```
password for level 12: 
```
JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
```
## Level 12
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir.  

First we make a directory '/tmp/tempo' and copy the file data.txt into the directory using `cp <source filename> <destination folder>` command.  
Then we enter the directory using `cd <foldername>` command.  
Then we move(rename) the file using `mv <source filename> <new filename>` command so it is easier to operate on the file contents.  
It is said that the data is in hexdump format. To read the contents from a hexdump of a file, `xxd -r <hexdump filename> <new filename>` is used.
Using `file` command tells that 'mycompdata' is a gzip type compressed file and 'mydata' is a text file.  
It is said that the file is compressed repeatedly. To retrieve the text, we need to decompress repeatedly.  
Since gzip files have the extension .gz, we rename 'mycompdata' as 'mycompdata.gz' using `mv` command.  
`gzip -d <compressed filename>` command is used to decompress a gzip file.  
Using `file` command again we get to know that the file has been decompressed into a bzip2 type file, so we rename the file as 'mycompdata.bz2'.  
`bzip2 -d mycompdata.bz2` is used to decompress the bzip2 file.  
Repeat this till we encounter a tar archive. Rename the file as 'mycompdata.tar'
`tar -xf <filename>` is used to extract a file from a tar archive.  
'data5.bin' is extracted, which is also a tar archive.  
Extracting files from data5.bin using `tar` and using `file` shows that data6.bin is a bzip2 type compressed file, which should be decompressed.  
Repeat until password is retrieved.  


## Commands:
```
ssh bandit12@bandit.labs.overthewire.org -p 2220
mkdir /tmp/tempo
cp data.txt /tmp/tempo
cd /tmp/tempo
mv data.txt mydata
xxd -r mydata mycompdata
file *
ls
mv mycompdata mycompdata.gz
gzip -d mycompdata.gz
file *
mv mycompdata.gz mycompdata.bz2
bzip2 -d mycompdata.bz2
file *
mv mycompdata mycompdata.gz
gzip -d mycompdata.gz
file *
mv mycompdata mycompdata.tar
tar -xf mycompdata.tar
ls
file *
tar -xf data5.bin
ls
file *
mv data6.bin data6.bin.bz2
file *
tar -xf data6.bin
ls
file *
mv data8.bin data8.bin.gz
gzip -d data8.bin.gz
file *
cat data8.bin
exit
```
password for level 13: 
```
wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
```
## Level 13
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on.  

After obtaining 'sshkey.private' from`ls`, we connect to the server using `ssh -i sshkey.private bandit14@localhost -p 2220` and read the given address using `cat` command.  

### Commands:
```
ssh bandit13@bandit.labs.overthewire.org -p 2220
ls
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
cat /etc/bandit_pass/bandit14
```
password for level 14: 
```
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
```
## Level 14
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.  
The Netcat (nc) command is a command-line utility for reading and writing data between two computer networks.  
`nc <hostname> <port>`   
`<shell prompt from host>`
### Commands:
```
ssh bandit14@bandit.labs.overthewire.org -p 2220
nc localhost 30000
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
exit
```
password for level 15:
```
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
```
## Level 15
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption. 
The openssl program is a command line program for using the various cryptography functions of OpenSSL's crypto library from the shell.
`openssl s_client -connect <hostname>:<port>`
### Commands:
```
ssh bandit15@bandit.labs.overthewire.org -p 2220
openssl s_client -connect localhost:30001
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
exit
```
password for level 16:
```
JQttfApK4SeyHwDlI9SXGR50qclOAil1
```
## Level 16
The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

`nmap` scans networks and ports.  
All these ports have a server listening on them:   
PORT      STATE SERVICE
31046/tcp open  unknown
31518/tcp open  unknown
31691/tcp open  unknown
31790/tcp open  unknown
31960/tcp open  unknown
Next we try to connect to each of the above ports with  
`openssl s_client -connect localhost:<port>`
31046 shows 'Secure regotiation is not supported'
31518 asks for the password but sends it back
31691 shows 'Secure renegotiation is not supported'
31790 asks for the password and returns an RSA PRIVATE KEY, which is the required port.  
We store the key in a file in the tmp directory.  
To read the key into the file, any text editor can be used.  
I have used vim for which we type `vim <filename>` and then press 'i' to enter into inserting mode. After typing, we press 'esc' to stop inserting.  
Then type `:wq` to save and exit the file.  (`:qa!` to exit without saving)  
Then when we try to connect to the next level with the private key, we get an error message saying 'Permissions 0664 for 'private16.key' are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
Load key "private16.key": bad permissions
bandit17@bandit.labs.overthewire.org: Permission denied (publickey).'
Which means we will have to change the permissions of the private key file.  
`chmod 400<filename>` gives the user read permission, and removes all other permissions.  
To store the password of level 17, we read the file '/etc/bandit_pass/bandit17'
password for level 17: 
```
VwOSWtCA7lRKkTfbr2IDh6awj9RNZM5e
```
### Commands: 
```
ssh bandit16@bandit.labs.overthewire.org -p 2220
nmap localhost -p31000-32000
openssl s_client -connect localhost:31046
openssl s_client -connect localhost:31518
openssl s_client -connect localhost:31691
openssl s_client -connect localhost:31790
mkdir /tmp/randomsshkey
cd /tmp/randomsshkey
touch private16.key
ls
vim private16.key
i
<insert the rsa private key>
<press escape>
:wq
ssh -i private16.key bandit17@bandit.labs.overthewire.org -p 2220
chmod 400 private16.key
ssh -i private16.key bandit17@bandit.labs.overthewire.org -p 2220
cat /etc/bandit_pass/bandit17
exit
```
## Level 17
There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

 `diff` command compares files line by line.  
 
### Commands:
```
ssh bandit17@bandit.labs.overthewire.org -p 2220
ls
diff passwords.old passwords.new






















