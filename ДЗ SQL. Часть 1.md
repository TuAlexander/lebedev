### Домашнее задание к занятию «SQL. Часть 1»

# Задание 1

SELECT DISTINCT district

FROM address

WHERE district LIKE 'K%a' AND district NOT LIKE 'K% %a';

![1](https://github.com/Niko1a/lebedev/assets/110035244/22ad5c25-e4c5-4872-83f1-2e9ee6009711)

# Задание 2

SELECT payment_id, customer_id, staff_id, rental_id, amount, CAST(payment_date AS DATE)

FROM payment

WHERE payment_date BETWEEN  '2005-06-15' AND '2005-06-18 23:59:59' AND amount > 10.00

ORDER BY payment_date  ASC;

![2](https://github.com/Niko1a/lebedev/assets/110035244/25e40e01-2f3d-4f07-a964-92d0115fdee0)

# Задание 3

SELECT rental_id, CAST(rental_date AS DATE),inventory_id, customer_id, staff_id 

FROM rental

ORDER BY rental_id DESC LIMIT 5;

![3](https://github.com/Niko1a/lebedev/assets/110035244/ad26e59a-60dc-456d-ba82-e2c02b48462d)


# Задание 4

SELECT active, customer_id, REPLACE(LOWER(first_name) , 'll', 'pp'), LOWER(last_name)

FROM customer

WHERE active = 1 AND (first_name LIKE 'Kelly' OR first_name  LIKE 'Willie');

![4](https://github.com/Niko1a/lebedev/assets/110035244/7a7ab034-50d1-4256-88ab-fb4d497a175a)

















