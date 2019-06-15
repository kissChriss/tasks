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






