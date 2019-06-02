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
