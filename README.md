# SQL
Learning SQL
В рамках домашнего задания, мною были созданы следующие запросы к MySQL:

Выведите информацию обо всех продуктах>> 	SELECT * FROM products;

Выведите информацию обо всех продуктах, произведенных Apple в категории Phones>>	SELECT * FROM products WHERE manufacturer = 'Apple' AND category = 'Phones';

Выведите названия продуктов и их стоимость, при условии что в названии содержатся буквы sa в любом месте>>	SELECT name, price FROM products WHERE name LIKE '%sa%';

Выведите названия продуктов и их стоимость, при условии того, что цена находится в диапазоне от 100 до 1000 долларов>>	SELECT name, price FROM products WHERE price BETWEEN 100 AND 1000;

Посчитайте сумму всех товаров, произведенных компанией Samsung. Название таблицы в результате запроса должно быть SAMSUNG TOTAL PRICE>>	SELECT COUNT(manufacturer) AS "SAMSUNG TOTAL PRICE" FROM products WHERE manufacturer = 'Samsung';

Выведите название всех товаров и их стоимость по убыванию>>	SELECT name, price FROM products ORDER BY price DESC;

Выведите названия всех производителей при условии, чтобы они не повторялись>>	SELECT DISTINCT manufacturer FROM products;

Выведите названия первых двух категорий продуктов, чтобы они не повторялись>>	SELECT DISTINCT category FROM products LIMIT 2;

Выведите названия продуктов при условии, что они состоят из 12 символов и их названия начинаются с A>>	SELECT name FROM products WHERE name LIKE 'A%' and LENGTH(name) = 12;

Посчитайте среднюю цену всех продуктов. Название таблицы в результате запроса должно быть PRODUCTS AVG PRICE>>	SELECT avg(price) AS PRODUCTS_AVG_PRICE FROM products;

Используя оператор IN, выведите названия и описание продуктов, у которых производитель Samsung и Huawei>>	SELECT name, description FROM products WHERE manufacturer IN ('Samsung', 'Huawei');

Используя оператор UNION, выведите информацию о названии товаров из таблицы products и номера заказов из таблицы orders>>	"SELECT name FROM products
UNION
SELECT order_id FROM orders;"

Используя оператор HAVING, посчитайте количество товаров в каждой категории, оставив только те категории, в которых количество товаров больше 15>>	SELECT count(product_id), category FROM products GROUP BY category HAVING count(product_id) > 15;

"Используя оператор CASE опишите следующую логику:
Выведите компанию, категорию, стоимость и название товара, а также следующий текстовое сообщение:

Если компания Apple, то в консоли должно вывестись ""Это продукт компании Apple"".

Если компания Samsung, то в консоли должно вывестись ""Это продукт компании Samsung"".

Если компания Huawei, то в консоли должно вывестись ""Это продукт компании  Huawei"".

Если компания Xiaomi, то в консоли должно вывестись ""Это продукт компании Xiaomi"".">>	"SELECT manufacturer, category, price, name, 
CASE
        WHEN manufacturer LIKE 'Apple' THEN 'Это продукт компании Apple'
        WHEN manufacturer LIKE 'Samsung' THEN 'Это продукт компании Samsung'
        WHEN manufacturer LIKE 'Huawei' THEN 'Это продукт компании Huawei'
        WHEN manufacturer LIKE 'Xiaomi' THEN 'Это продукт компании Xiaomi'
END AS info_manufacturer
FROM products;"

Выведите логин вашего пользователя, номера его заказов и их стоимость (таблицы users и orders)>>	"SELECT users.login, orders.order_id, orders.total
FROM users
INNER JOIN orders
ON users.user_id = orders.user_id;"	

Выведите номера всех заказов, названия товаров в них и их количество (таблицы order_items и products)>>	"SELECT order_items.order_item_id, order_items.quantity, products.name
FROM order_items
LEFT JOIN products
ON order_items.product_id = products.product_id;"

Выведите логины всех пользователей и номера заказов, вне зависимоcти от того, есть ли у них заказ или нет (таблицы users и orders)>>	"SELECT users.login, orders.order_id
FROM users
LEFT JOIN orders
ON users.user_id = orders.user_id;"	

Выведите номера оплаченных заказов и название всех товаров, вне зависимоcти от того, упоминаются ли товары в оплаченных заказах (таблицы products и order_items_paid)>>	"SELECT order_items_paid.order_id, products.name 
FROM order_items_paid 
RIGHT JOIN products  
ON order_items_paid.product_id = products.product_id;"	

Используя вложенный запрос выведите названия и стоимость товаров, у которых стоимость товара больше, чем стоимость товара "Samsung Active 5" из таблицы products	"SELECT name, price
FROM products
WHERE price > (SELECT price FROM products WHERE name = 'Samsung Active 5');"	
