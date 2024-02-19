# SQL1

-- SQL 1. Ödev

1-) film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.

SELECT title, description FROM film; 

2-) film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.

SELECT * FROM film
WHERE length > 60 AND < 75;

3-) film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.

SELECT * FROM film
WHERE rental_rate = 0.99 AND replacement_cost = 12.99 OR replacement_cost = 28.99;

4-) customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

SELECT last_name FROM customer
WHERE first_name = 'Mary';

5-) film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

SELECT * FROM film
WHERE NOT length>50 AND NOT (rental_rate=2.99 OR rental_rate=4.99);


--SQL 2. Ödev

1) film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)

SELECT * FROM film WHERE replacement cost BETWEEN 12.99 AND 16.99;

2-) actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

SELECT first_name, last_name FROM actor 
WHERE first_name IN ('Penelope','Nick','Ed');

3-) film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

SELECT * FROM film
WHERE rental_rate IN(0.99,2.99,4.99) AND replacement_cost IN(12.99,15.99,28.99);

-- SQL 3. Ödev

1-) country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

select country from country 
where country like 'a%a';

2) country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

select country from country
SELECT country FROM country WHERE length (country) >=6 AND country LIKE '%n' ;

3) film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

SELECT title FROM film WHERE title ILIKE '%t%t%t%t%' ;

4) film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

SELECT * FROM film WHERE title LIKE 'C%' AND length(title) > 90 AND rental_rate = 2.99 ;

-- SQL 4. Ödev

1) film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

select distinct replacement_cost form film;

2) film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

select count(distinct replacement_cost) from film;

3) film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

SELECT COUNT(DISTINCT title) FROM film WHERE title LIKE 'T%' AND rating = 'G' ;

4) country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

select count(country) from country where length(country) = 5;

5) city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?

SELECT COUNT(*) FROM city WHERE (city) ILIKE '%r' ;

-- SQL 5. Ödev

film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

select title from film 
where title like '%n'
order by length desc
limit 5;

film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.

SELECT title FROM film WHERE title LIKE '%n' ORDER BY length OFFSET 5 LIMIT 5;

customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

SELECT * FROM customer WHERE store_id = 1 ORDER BY last_name DESC LIMIT 4;

-- SQL 6. Ödev

film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

SELECT AVG(rental_rate) FROM film;

film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?

select count(title) from film 
where title like 'C%'

film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

select max(length) from film
where rental_rate = 0.99

film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

SELECT COUNT(DISTINCT replacement_cost) FROM film WHERE length > 150;
















