## Задание 1   

Запрос, формирующий выборку по условию задания  
```sql
SELECT model.name AS "Model", brand.name AS "Brand", os.name AS "OS" 
FROM model 
INNER JOIN brand ON model.brand = brand.id
INNER JOIN os ON model.os = os.id
```

## Задание 2  

Приложение создало 2 новые таблицы - migrations и users  
![new_tables](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/DB-screens/new_tables.png)  

В таблице migrations была создана одна строка  
![migrations](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/DB-screens/select_from_migrations.png)

А в таблице users пока нет новых строк  
![users](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/DB-screens/select_from_users.png)

Файл compose.yaml доступен по [ссылке](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/compose.yaml)  


