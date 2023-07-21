# neoflex-linux-rsafin-task1

## Задание 1-2
Подготовлены виртуальные машины в соответствии с ТЗ  
**Main** -  2 CPU / 8 GB RAM / 50 GB SSD  
**Infra** - 1 CPU / 2 GB RAM / 40 GB HDD  

## Задание 3 
Учетную записть **neoflex** с правами администратора создал на обеих VM еще на этапе установки ОС. 
На обе VM загрузил свой ключ, настроил вход. Далее поменял порт SSH на 33555, отключил возможность входа по паролю и вход по SSH для root пользователя. 
Файрвол также настроил. Для удобства задал у себя в hosts соответствие IP машин их именам 
`ssh neoflex@main -p 33555`

## Задание 4
VM и приватный ключ доступны по ссылке  
https://drive.google.com/drive/folders/1oZOJ3XSfzA7ky3hr09QI7X6HMGR9NsLX?usp=sharing

Приватный ключ в файле id_rsa  
Порт SSH: 33555  

## Задание 5
RPM-based системы обычно идут с уже включенным ACL, который позволяет легко решить поставленную задачу.   

Создаем пользователей   
![useradd](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/useradd.png)

Создаем директории и файл  
![mkdir](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/dirs%26files.png)

Задаем правила ACL  
![setfacl](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/setfacl.png)

Смотрим правила ACL  
![getfacl](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/getfacl.png)

Hello Neoflex  
![Hello Neoflex](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/hello_neoflex.png)
