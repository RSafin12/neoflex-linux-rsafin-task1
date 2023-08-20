-- Написать запрос по шаблону, к демонстрационной базе данных, использовать любую таблицу на ваше усмотрение, главный критерий код запроса должен быть рабочим и возвращать строки, код запроса приложить в качестве результата выполненого ДЗ, самостоятельно код запроса выполнить и проанализировать результат.  


--1  
SELECT city, airport_name, airport_code  
FROM airports a;  
 
--2  
SELECT DISTINCT ticket_no, book_ref  
FROM tickets t;  

--3  
SELECT ticket_no, fare_conditions, amount  
FROM ticket_flights tf  
WHERE amount >= 23900;  

--4 использовать как AND так и OR в одном условии.  
SELECT *  
FROM flights f  
WHERE arrival_airport  = 'LED' OR arrival_airport = 'UFA' AND status = 'Delayed';  

--5  
SELECT  airport_name, city, airport_code  
FROM airports a  
WHERE airport_code IN ('LED', 'UFA', 'CEK');  

--6  
SELECT status, arrival_airport, scheduled_arrival  
FROM flights f  
WHERE actual_arrival BETWEEN '2016-09-13' AND '2016-12-13';  

--7  
SELECT ticket_no, passenger_name, contact_data  
FROM tickets t  
WHERE passenger_name LIKE 'TATYANA%'  

--8 Использовать одновременно ASC и DESC для разных столбцов  
SELECT aircraft_code, model  
FROM aircrafts a  
WHERE "range" > 1200  
ORDER BY aircraft_code  ASC, model DESC;  

--9  
SELECT sum(total_amount), book_ref  
FROM bookings b  
WHERE book_date = '2016-09-02'  
GROUP BY book_ref;  

--10  
SELECT count(passenger_id)  
FROM tickets t  
WHERE passenger_name LIKE 'ANNA%';  

--11  
SELECT sum(total_amount), book_ref  
FROM bookings b  
WHERE book_date = '2016-09-02'  
GROUP BY book_ref   
HAVING sum(total_amount) >= 40000;  



-- Аналогично предыдущему заданию, по шаблонам написать рабочие запросы к демонстрационной базе данных.  

-- создание таблицы, не менее 4х колонок разного типа, 1 колонка первичный ключ, одна необнуляймая  
 CREATE TABLE souvenir (  
   item_code int NOT NULL,  
   item_description varchar(50),  
   paid boolean,  
   purchase_date date,  
   PRIMARY KEY (item_code)  
 );  

-- удаление таблицы  
DROP TABLE souvenir;  

-- создание индекса  
CREATE UNIQUE INDEX customer_index  
ON souvenir (item_code);   

-- удаление индекса  
--ALTER TABLE tableName  
DROP INDEX customer_index;  

-- получение описания структуры таблицы  
-- DESC souvenir;  - не работает, альтернатив:  

SELECT column_name, column_default, data_type  
FROM INFORMATION_SCHEMA.COLUMNS  
WHERE table_name = 'souvenir';  

-- очистка таблицы   
TRUNCATE TABLE souvenir;  

-- выбрать одно из вариантов: добавление/удаление/модификация колонок  
ALTER TABLE souvenir ADD item_customer varchar(50);  

-- переименование таблицы   
ALTER TABLE souvenir RENAME TO gifts;  

-- вставка значений  
INSERT INTO gifts (item_code, item_description, paid, purchase_date)  
VALUES (1, 'doll', 'YES', '2016-10-13');  

-- обновление записей  
UPDATE gifts  
SET item_code = 2, item_description = 'bear'  
WHERE paid = 'YES';  

-- удаление записей  
DELETE FROM gifts  
WHERE purchase_date = '2016-10-13';  
