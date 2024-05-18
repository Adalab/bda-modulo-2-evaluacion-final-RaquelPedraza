USE sakila;


 /*__________Ejercicio 1__________*/ 

SELECT DISTINCT title
FROM film;

/*__________Ejercicio 2__________*/ 
 
SELECT title
FROM film
WHERE rating = 'PG-13';


/*__________Ejercicio 3__________*/ 

SELECT title, description
FROM film
WHERE description LIKE '%amazing%';


/*__________Ejercicio 4__________*/ 

SELECT title
FROM film
WHERE length > 120;


/*__________Ejercicio 5__________*/ 

SELECT first_name, last_name
FROM actor;


/*__________Ejercicio 6__________*/ 

SELECT first_name, last_name
FROM actor
WHERE last_name LIKE '%Gibson%';


/*__________Ejercicio 7__________*/ 
 
SELECT first_name, last_name
FROM actor
WHERE actor_id BETWEEN 10 AND 20;


/*__________Ejercicio 8__________*/ 

SELECT title
FROM film
WHERE rating NOT IN ('R', 'PG-13');

  
/*__________Ejercicio 9__________*/ 

SELECT rating, COUNT(*) AS total_movies
FROM film
GROUP BY rating;

   
/*__________Ejercicio 10__________*/ 

SELECT c.customer_id, c.first_name, c.last_name, COUNT(r.rental_id) AS total_rented_movies
FROM customer c
LEFT JOIN rental r ON c.customer_id = r.customer_id
GROUP BY c.customer_id, c.first_name, c.last_name;

    
/*__________Ejercicio 11__________*/ 

SELECT c.name AS category_name, 
       (SELECT COUNT(*)
        FROM film_category fc
        JOIN film f ON fc.film_id = f.film_id
        JOIN inventory i ON f.film_id = i.film_id
        JOIN rental r ON i.inventory_id = r.inventory_id
        WHERE fc.category_id = c.category_id) AS total_rentals
FROM category c;

     
/*__________Ejercicio 12__________*/ 

SELECT rating, AVG(length) AS average_duration
FROM film
GROUP BY rating;

      
/*__________Ejercicio 13__________*/

SELECT a.first_name, a.last_name
FROM actor a
JOIN film_actor fa ON a.actor_id = fa.actor_id
JOIN film f ON fa.film_id = f.film_id
WHERE f.title = 'Indian Love';
 
       
/*__________Ejercicio 14__________*/ 

-- subquery
SELECT title
FROM film
WHERE film_id IN (
    SELECT film_id
    FROM film
    WHERE description LIKE '%dog%' OR description LIKE '%cat%'
);

        
/*__________Ejercicio 15__________*/ 

SELECT actor_id, first_name, last_name
FROM actor
WHERE actor_id NOT IN (
    SELECT DISTINCT actor_id
    FROM film_actor
);

         
/*__________Ejercicio 16__________*/ 

SELECT title
FROM film
WHERE release_year BETWEEN 2005 AND 2010;

          
/*__________Ejercicio 17__________*/ 

SELECT f.title
FROM film f
JOIN film_category fc ON f.film_id = fc.film_id
JOIN category c ON fc.category_id = c.category_id
WHERE c.name = 'Family';

           
/*__________Ejercicio 18__________*/ 

SELECT a.first_name, a.last_name
FROM actor a
JOIN film_actor fa ON a.actor_id = fa.actor_id
GROUP BY a.actor_id
HAVING COUNT(*) > 10;

            
/*__________Ejercicio 19__________*/ 
             
/*__________Ejercicio 20__________*/ 
	
/*__________Ejercicio 21__________*/ 
               
/*__________Ejercicio 22__________*/ 
                
/*__________Ejercicio 23__________*/ 

/*____________BONUS____________*/ 
             
/*__________Ejercicio 24__________*/ 
              
/*__________Ejercicio 25__________*/ 
               