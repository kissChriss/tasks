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
## Blending
**Проверка пароля**  
Введите правильный пароль на [сайте](https://regexp_pass.training.hackerdom.ru/).  
Исходник:  
```php
<html>
<head>
    <title>РџСЂРѕРІРµСЂРєР° РїР°СЂРѕР»СЏ</title>
    <link rel='stylesheet' href='style.css' type='text/css'>
    <meta charset="utf-8" />
</head>
<body>

<?php
require 'flag.php';

if (isset ($_GET['password'])) {
	if (ereg ("^[a-zA-Z0-9]+$", $_GET['password']) === FALSE)
		echo '<p class="alert">You password must be alphanumeric</p>';
	else if (strpos ($_GET['password'], '--') !== FALSE)
		die('Flag: ' . $flag);
	else
		echo '<p class="alert">Неверный пароль</p>';
}
?>

<section class="login">
        <div class="title">
                <a href="./index.txt">РСЃС…РѕРґРЅРёРє</a>
        </div>

        <form method="get">
                <input type="text" required name="password" placeholder="РџР°СЂРѕР»СЊ" /><br/>
                <input type="submit" value="Р’РѕР№С‚Рё"/>
        </form>
</section>
</body>
</html>
```
Null Byte:
```https://regexp_pass.training.hackerdom.ru/?password=pass%00--```

