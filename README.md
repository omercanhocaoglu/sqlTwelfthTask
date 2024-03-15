# sqlTwelfthTask
## Bu repo [Patika.dev](https://www.patika.dev) tarafından verilen `SQL` ödevini içermektedir.
---
### Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.
### 1- film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?
- SELECT title, length ,(SELECT ROUND (AVG (length), 0) FROM film) FROM film
- WHERE length > 115
- ORDER BY length ASC;
### 2- film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?
- SELECT title, rental_rate, (SELECT MAX (rental_rate) FROM film) FROM film
- WHERE rental_rate = ALL
- (
- SELECT rental_rate from film
- WHERE rental_rate = 4.99
- );
### 3- film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.
- SELECT title, rental_rate, replacement_cost,
- (SELECT MIN( rental_rate ) FROM film),
- (SELECT MIN( replacement_cost ) FROM film)
- FROM film
- WHERE rental_rate = ALL 
- (SELECT rental_rate FROM film WHERE rental_rate = 0.99 ) 
- AND 
- replacement_cost = ALL
- ( SELECT replacement_cost FROM film WHERE replacement_cost = 9.99 );
### 4- payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.
- SELECT customer_id, (SELECT MAX(amount) FROM payment) FROM payment
- WHERE amount = ALL
- (
- SELECT amount FROM payment
- WHERE amount = 11.99
- );
