# banditdoc
This repository contains writeup for helping in solving bandits- by Sapthami

## Level 0
`ssh` is used for remote login into a server. It can login into different port numbers deployed on a server and it will act as a client to that server.  
`ls` shows the list of available files  
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
ls
cat data.txt | tr '[A-Za-z]' '[N-ZA-Mn-za-m]'
```
password for level 12: 
```
JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
```
## Level 12
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)



