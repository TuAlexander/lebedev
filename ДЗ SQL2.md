# Домашнее задание к занятию «SQL. Часть 2»


### Задание 1

    SELECT CONCAT(s.first_name, ' ' , s.last_name) AS Employee, c.city AS City, COUNT(c2.store_id) AS Number_of_customers
    FROM staff s
    JOIN store s2 ON s.store_id = s2.store_id
    JOIN address a ON s2.address_id = a.address_id
    JOIN city c ON a.city_id = c.city_id
    JOIN customer c2 ON s2.store_id = c2.store_id
    GROUP BY s.staff_id
    HAVING  COUNT(c2.store_id) > 300;

![1](https://github.com/Niko1a/lebedev/assets/110035244/c60ccd89-a10e-49d7-b75b-6089f3ffcde1)


### Задание 2

    SELECT COUNT(film_id) AS 'Number of films which duration is above average (115)'  
    FROM film f
    WHERE `length` > (SELECT AVG(`length`) FROM film f2)

![2](https://github.com/Niko1a/lebedev/assets/110035244/14dc53e9-45fa-437d-9da8-9241b6d14939)


### Задание 3
  
    SELECT month(p.payment_date) AS 'Highest Amount of Payments Received Month', count(r.rental_id) 'Number of Rentals'
    FROM payment p INNER JOIN 
         rental r ON p.rental_id = r.rental_id 
         GROUP BY  month(payment_date)
    ORDER BY  sum(p.amount) DESC
    LIMIT 1

![3](https://github.com/Niko1a/lebedev/assets/110035244/aa786acc-5a70-451a-8da3-9475b32a7e09)











