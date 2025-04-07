---
tags:
  - linux
  - bash
  - cheatsheet
aliases:
  - Linux Commands
  - Linux Cheatsheet
date: 2025-03-30
---

# name of command

## description of command's functions

### useful specific usages of command with arguments

commands as inputted to cli

# cat

## concatenates files contents to the terminal

## concatenate with line numbers

```BASH
cat -n joyce.txt
```

# du

### shows the size of all files in the current directory

`du -sh *

# find

### find files in current directory modified in last 24 hours

`find . -maxdepth 1 -mtime -1`

### find file named main.py in directory with specific name

`find ./Sync -name main.py`

### find file with .py extension

`find ./Sync -name '*.py'

# grep

## used to search text and strings in a given file

## find string within current folder, n shows relative line number and r recursively searches subdirectories, . is current directory

```BASH
grep -nr 'tab-desk' .
```

### search any line that contains word in filename

grep 'word' filename.txt

### perform case-insensitive search for word in file

grep -i 'word' filename.txt

### look in all files in current directory and in all subdirectories for word

grep -R 'thank'

### search and display number of times string appears in file

grep -c 'thank' file.txt

### find and display all lines that contain a word

grep -F 'thank' file.txt

### find and display all lines that contain a word as a whole word(will not display thanks)

grep -F -w 'thank' file.txt

# less

## view full file in terminal with scrolling and search controls, vim controls (j, k, q, / to search)

# permissions

## -rwxrwxrwx first character is - for file, d for directory, l is for symlink. r is read, w is write, and x is execute, first set is for user, second set is for group and third set is for others outside user and group. - means permission revoked

### add john to debian-transmission group

sudo usermod -a -G debian-transmission john

### change the folder ownership

sudo chgrp debian-transmission /mnt/imp/Media/Movies/Idiocracy_2006

### grant write access to the group

sudo chmod 770 /mnt/imp/Media/Movies/Idiocracy_2006

### grant access for plex to access files

chmod 755 /plexmedialibrary

### add existing user to a secondary group

usermod -a -G GROUP USER

# rsync

### copies file to new directory and shows progress

rsync --progress file.txt ~/john/

### copies file to new directory, renames file and shows progress

rsync --progress file.txt ~/john/target.txt

# scp

### copies file from from mbrain to current directory away from house

scp -P 570 97.120.181.83:/mnt/backup/sambashare/originals/IMG_1868.jpg ./

# sed

## stream editor that works on piped input or files of text. Instructions are provided and it works through the text. Select txt, substitute text, add lines to text, delete lines from text, modify (or preserve) an original file.

## echo text to sed through pipe and substitute portion of the text

```BASH
echo howtogonk | sed 's/on/ee/'
```

## select and display lines 1-4 of a file

```BASH
sed -n '1,4p' joyce.txt
```

### select multiple line selections in a file and display

```BASH
sed -n -e '1,4p' -e '24,27p' joyce.txt
```

## substitute text in a file, g for globally as to not stop at the first occurence of a line, i for case insensitive (tobechanged or Tobechanged), and p to print the output to the terminal

```BASH
sed -n 's/tobechanged/substitute/gip' joyce.txt
```

## substitute text in a file using multiple letters as the selector

```BASH
sed -n 's/[Dd]ay/week/gp' joyce.txt
```

## insert text after a line that begins with a specified string

```BASH
sed '/JIM/a --> Inserted!' joyce.txt
```

# sshfs

### mount dooky to ~/mnt on WSL

sshfs -p 570 192.168.0.16:/mnt/dooky /home/john/mnt
umount /home/john/mnt

### mount ~/ on Humbert to ~/Humbert on WSL

sshfs -p 571 192.168.0.11:/home/john /home/john/Humbert

# service

## reload vs restart

### *restart* shuts the program down and restarts, rewriting settings to original state

### *reload* instructs the program to reload its configuration

sudo service transmission-daemon restart
sudo service transmission-daemon reload

## start a service

sudo service transmission-daemon start

## stop a service

sudo service transmission-daemon stop

## status

sudo service transmission-daemon status

# ufw

## unblock port 9260

sudo ufw allow 9260

## status

sudo ufw status
sudo ufw status numbered