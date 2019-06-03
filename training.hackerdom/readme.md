https://training.hackerdom.ru/board/  

## Hash
**SHA-1**  
SHA1(пароль) = 'a58dc2cfc5a93134666c607fbc5d6e961254214a'. Пароль состоит ровно из восьми цифр.  
```python
import hashlib

hash_string = 'a58dc2cfc5a93134666c607fbc5d6e961254214a'

for i in range (10000000, 99999999):
	m = hashlib.sha1(str(i)).hexdigest()
	print (m)
	if m == hash_string:
		print('Did it! Number is ' + str(i))
		break
```
