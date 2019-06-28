```ssh bandit_@bandit.labs.overthewire.org -p 2220```

## Bandit Level 0 → Level 1
The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1  
**Answer:**```cat readme```  

## Bandit Level 1 → Level 2  
The password for the next level is stored in a file called - located in the home directory  
**Answer:**```cat ./-```

## Bandit Level 2 → Level 3  
The password for the next level is stored in a file called spaces in this filename located in the home directory  
**Answer:**```cat spaces\ in\ this\ filename```  

## Bandit Level 3 → Level 4  
The password for the next level is stored in a hidden file in the inhere directory.  
**Answer:**```cat inhere/.hidden```  

## Bandit Level 4 → Level 5  
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.  
**Answer:**```cat inhere/* | strings```

## Bandit Level 5 → Level 6  
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
- human-readable  
- 1033 bytes in size  
- not executable  
**Answer:** ```find ./inhere/ -ls```   
```cat ./inhere/maybehere07/.file2```  

## Bandit Level 6 → Level 7  
The password for the next level is stored somewhere on the server and has all of the following properties:  
- owned by user bandit7  
- owned by group bandit6  
- 33 bytes in size  
**Answer:** ```find ./ -user bandit7 -group bandit6```  
```cat ./var/lib/dpkg/info/bandit7.password```  

## Bandit Level 7 → Level 8
The password for the next level is stored in the file data.txt next to the word millionth  Bandit Level 8 → Level 9
**Answer:**```cat data.txt | grep millionth```  

## Bandit Level 8 → Level 9
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once  
**Answer:** ```sort data.txt | uniq -u```

## Bandit Level 9 → Level 10
The password for the next level is stored in the file data.txt in one of the few human-readable strings, beginning with several ‘=’ characters.  
**Answer:** ```strings data.txt | grep =```

## Bandit Level 10 → Level 11  
The password for the next level is stored in the file data.txt, which contains base64 encoded data  
**Answer:** ```base64 -d data.txt ```

## Bandit Level 11 → Level 12  
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions  
**Answer:** ```cat data.txt | tr '[a-z]' '[n-za-m]' | tr '[A-Z]' '[N-ZA-M]'```

## Bandit Level 12 → Level 13  
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)  
**Answer:**```cd /tmp/```  
```mkdir tmp_folder```  
```cd tmp_folder```  
```cp /home/bandit12/data.txt /tmp/tmp_folder/data.txt```  
```xxd -r data.txt > new_data```  
```file new_data```   
new_data: gzip compressed data, was "data2.bin", last modified: Tue Oct 16 12:00:23 2018, max compression, from Unix  
```mv new_data new_data.gz```  
```file new_data```  
new_data: bzip2 compressed data, block size = 900k  
```mv new_data new_data.bz2```  
```bzip2 -d new_data.bz2```  
```file new_data```  
new_data: gzip compressed data, was "data4.bin", last modified: Tue Oct 16 12:00:23 2018, max compression, from Unix  
```mv new_data new_data.gz```  
```gunzip -k new_data.gz```  
```file new_data```  
new_data: POSIX tar archive (GNU)  
```mv new_data new_data.tar```  
```tar -xvf new_data.tar```  
```file data5.bin```  
data5.bin: POSIX tar archive (GNU)  
```mv data5.bin new_data1.tar```  
```tar -xvf new_data1.tar```  
```file data6.bin```  
data6.bin: bzip2 compressed data, block size = 900k  
```mv data6.bin new_data2.bz2```  
```bzip2 -d new_data2.bz2```  
```file new_data2```  
new_data2: POSIX tar archive (GNU)  
```mv new_data2 new_data2.tar```  
```tar -xvf new_data2.tar```  
```file data8.bin```  
data8.bin: gzip compressed data, was "data9.bin", last modified: Tue Oct 16 12:00:23 2018, max compression, from Unix  
```mv data8.bin data8.gz```  
```gunzip -k data8.gz```  
```file data8```  
data8: ASCII text  
```cat data8```  

## Bandit Level 13 → Level 14  
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on  
**Answer:**
```touch file.txt```  
```vi file.txt```  
```  
----RSA PRIVATE KEY----
```  
```chmod 600 file.txt```  
```ssh -i file.txt bandit14@bandit.labs.overthewire.org -p 2220```  
```cat /etc/bandit_pass/bandit14```  

## Bandit Level 14 → Level 15  
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.  
**Answer:**```nc -v localhost 30000```  
```<password of the current level>```  

## Bandit Level 15 → Level 16  
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…  
**Answer:**```ncat -C --ssl localhost 30001```  

## Bandit Level 16 → Level 17  
The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.  
**Answer:**```nc -zv localhost 31000-32000```  
```ncat -C --ssl localhost 31790```  

## Bandit Level 17 → Level 18  
There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new  
NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19  
**Answer:**```touch file.txt```  
```vi file.txt```  
```  
----RSA PRIVATE KEY----
```  
```chmod 600 file.txt```  
```ssh -i file.txt bandit17@bandit.labs.overthewire.org -p 2220```  
```diff passwords.new passwords.old```  

## Bandit Level 18 → Level 19  
The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.  
**Answer:**```ssh bandit18@bandit.labs.overthewire.org -p 2220 cat /home/bandit18/readme```  

## Bandit Level 19 → Level 20  
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.  
**Answer:**```./bandit20-do cat /etc/bandit_pass/bandit20```  

## Bandit Level 20 → Level 21  
There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).  
NOTE: Try connecting to your own network daemon to see if it works as you think  
**Answer:**``` echo "GbKksEFF4yrVs6il55v6gwY5aVje5f0j" | nc -l -p 29999```  
2nd terminal: ```ssh bandit20@bandit.labs.overthewire.org -p 2220```  
```./suconnect 29999```  

## Bandit Level 21 → Level 22  
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.  
**Answer:** ```cd /etc/cron.d/```  
```cat cronjob_bandit22```  
```cat /usr/bin/cronjob_bandit22.sh```  
```cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv```  

## Bandit Level 22 → Level 23  
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.  
NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.  
**Answer:**```cd /etc/cron.d/```  
```cat cronjob_bandit23```  
```echo I am user bandit23 | md5sum | cut -d ' ' -f 1```  
```cat /tmp/8ca319486bfbbc3663ea0fbe81326349```  

## Bandit Level 23 → Level 24
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.  

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!  

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…  
**Answer:**```cd /var/spool/bandit24/```  
```mkdir m0pk08k4/```  
```vi m0pk08k4/script.sh```  
```
#!/bin/sh
cat /etc/bandit_pass/bandit24 >> /var/spool/bandit24/m0pk08k4/pass
```  

```chmod 650 /m0pk08k4/script.sh```  
```cp /m0pk08k4/script.sh /var/spool/bandit24/```  

## Bandit Level 24 → Level 25  
A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.  
**Answer:** ```vi script.sh```  
```
#!/bin/sh
for i in {0000..9999}
do
echo "<pass_of_current_level> $i >> file.txt"
done
```  
```chmod 650 script.sh```  
```bash script.sh```   
```tac file.txt | nc localhost 30002```  

## Bandit Level 25 → Level 26    
Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.
**Answer** It's unreal, who have made that  

## Bandit Level 26 → Level 27  
Good job getting a shell! Now hurry and grab the password for bandit27!  

















