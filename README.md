# banditdoc
This repository contains writeup for helping in solving bandits by Sapthami
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
cat ./maybehere07/,file2
````
password for level 6: 
````
P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
````
