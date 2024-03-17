

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

--SQL 7. Ödev

film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

select rating from film
group by rating;

film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.,

select replacemet_cost count(*) from film
group by replacement_cost
having count(*) > 50

customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?

select store_id count(*) from customer
customer by store_id;

city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.

SELECT country_id, COUNT(*) FROM city
GROUP BY country_id
ORDER BY COUNT(*) DESC
LIMIT 1;

-- 8. SQL Ödevi

 test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

 CREATE TABLE employee (
  id INTEGER,
  name VARCHAR(50) NOT NULL,
  birthday DATE,
  email VARCHAR(100)
);

2) Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.

insert into MOCK_DATA (id, name, birthday, email) values (1, 'Vassily', '1984-08-24', 'vfaucherand0@360.cn');
insert into MOCK_DATA (id, name, birthday, email) values (2, 'Kristine', '1957-04-09', 'kcuttings1@constantcontact.com');
insert into MOCK_DATA (id, name, birthday, email) values (3, 'Dela', '1992-02-08', 'dgilliam2@arstechnica.com');
insert into MOCK_DATA (id, name, birthday, email) values (4, 'Annadiana', '1957-03-30', 'ahurne3@deliciousdays.com');
insert into MOCK_DATA (id, name, birthday, email) values (5, 'Roseline', '1967-05-02', 'rdober4@pinterest.com');
insert into MOCK_DATA (id, name, birthday, email) values (6, 'Emelita', '1995-09-08', 'etorrent5@liveinternet.ru');
insert into MOCK_DATA (id, name, birthday, email) values (7, 'Remus', '1926-12-19', 'rflaverty6@acquirethisname.com');
insert into MOCK_DATA (id, name, birthday, email) values (8, 'Maure', '1945-05-19', 'mtwist7@wikia.com');
insert into MOCK_DATA (id, name, birthday, email) values (9, 'Stacy', '1964-08-17', 'scastelli8@noaa.gov');
insert into MOCK_DATA (id, name, birthday, email) values (10, 'Michell', '1931-11-20', 'mbrogiotti9@dedecms.com');
insert into MOCK_DATA (id, name, birthday, email) values (11, 'Reinwald', '1980-01-21', 'rantcliffa@ucla.edu');
insert into MOCK_DATA (id, name, birthday, email) values (12, 'Barny', '1931-04-11', 'bgrierb@linkedin.com');
insert into MOCK_DATA (id, name, birthday, email) values (13, 'Ellery', '1988-04-21', 'emadlec@pagesperso-orange.fr');
insert into MOCK_DATA (id, name, birthday, email) values (14, 'Evy', '1933-10-07', 'ebocked@cnbc.com');
insert into MOCK_DATA (id, name, birthday, email) values (15, 'Erhard', '1989-03-09', 'ematkine@wp.com');
insert into MOCK_DATA (id, name, birthday, email) values (16, 'Barbara', '1952-09-05', 'bbeavingtonf@goo.gl');
insert into MOCK_DATA (id, name, birthday, email) values (17, 'Daisey', '1963-12-27', 'dbourcqg@weibo.com');
insert into MOCK_DATA (id, name, birthday, email) values (18, 'Alis', '1948-01-29', 'ahonackh@chicagotribune.com');
insert into MOCK_DATA (id, name, birthday, email) values (19, 'Delcina', '1924-12-21', 'dspearingi@uol.com.br');
insert into MOCK_DATA (id, name, birthday, email) values (20, 'Aurie', '1979-01-08', 'acomminj@a8.net');
insert into MOCK_DATA (id, name, birthday, email) values (21, 'Eliot', '1959-04-08', 'ecrosek@sciencedaily.com');
insert into MOCK_DATA (id, name, birthday, email) values (22, 'Gerladina', '1938-07-15', 'gactonl@hhs.gov');
insert into MOCK_DATA (id, name, birthday, email) values (23, 'Skipton', '1934-05-08', 'sdautrym@si.edu');
insert into MOCK_DATA (id, name, birthday, email) values (24, 'Aubrey', '1951-05-22', 'astuddersn@usatoday.com');
insert into MOCK_DATA (id, name, birthday, email) values (25, 'Isabella', '1954-09-21', 'ichrishopo@twitpic.com');
insert into MOCK_DATA (id, name, birthday, email) values (26, 'Maribelle', '1964-06-18', 'mpuddephattp@blogger.com');
insert into MOCK_DATA (id, name, birthday, email) values (27, 'Garey', '1945-11-16', 'gbrookeq@thetimes.co.uk');
insert into MOCK_DATA (id, name, birthday, email) values (28, 'Orella', '1927-12-20', 'orookesbyr@engadget.com');
insert into MOCK_DATA (id, name, birthday, email) values (29, 'Gerianne', '1950-11-06', 'ggairs@tinyurl.com');
insert into MOCK_DATA (id, name, birthday, email) values (30, 'Rustin', '1933-10-24', 'rcheccuzzit@phoca.cz');
insert into MOCK_DATA (id, name, birthday, email) values (31, 'Krystalle', '1969-03-01', 'kvalentinettiu@huffingtonpost.com');
insert into MOCK_DATA (id, name, birthday, email) values (32, 'Jenda', '1972-09-04', 'jspencleyv@nymag.com');
insert into MOCK_DATA (id, name, birthday, email) values (33, 'Guntar', '1951-12-03', 'gparramw@meetup.com');
insert into MOCK_DATA (id, name, birthday, email) values (34, 'Liesa', '1970-12-15', 'lbraidx@rakuten.co.jp');
insert into MOCK_DATA (id, name, birthday, email) values (35, 'Orran', '1968-05-19', 'ohankinsy@mozilla.org');
insert into MOCK_DATA (id, name, birthday, email) values (36, 'Frasier', '1983-08-23', 'fladenz@ucoz.ru');
insert into MOCK_DATA (id, name, birthday, email) values (37, 'Marwin', '1995-04-06', 'mvlasyuk10@imageshack.us');
insert into MOCK_DATA (id, name, birthday, email) values (38, 'Olia', '1925-02-22', 'opierrepont11@guardian.co.uk');
insert into MOCK_DATA (id, name, birthday, email) values (39, 'Peter', '1933-03-01', 'ppym12@statcounter.com');
insert into MOCK_DATA (id, name, birthday, email) values (40, 'Lynsey', '1993-07-27', 'ljarrett13@ucsd.edu');
insert into MOCK_DATA (id, name, birthday, email) values (41, 'Naomi', '1982-03-19', 'ngoosnell14@acquirethisname.com');
insert into MOCK_DATA (id, name, birthday, email) values (42, 'Bear', '1961-02-11', 'bkeatley15@php.net');
insert into MOCK_DATA (id, name, birthday, email) values (43, 'Frayda', '1963-05-04', 'fchittock16@google.com');
insert into MOCK_DATA (id, name, birthday, email) values (44, 'Kele', '1984-10-12', 'kkliemchen17@time.com');
insert into MOCK_DATA (id, name, birthday, email) values (45, 'Tull', '1921-11-24', 'twinspear18@geocities.com');
insert into MOCK_DATA (id, name, birthday, email) values (46, 'Gabie', '1972-09-02', 'gausher19@domainmarket.com');
insert into MOCK_DATA (id, name, birthday, email) values (47, 'Debra', '1959-09-27', 'djaouen1a@github.com');
insert into MOCK_DATA (id, name, birthday, email) values (48, 'Gabie', '1976-09-22', 'ghaslam1b@t-online.de');
insert into MOCK_DATA (id, name, birthday, email) values (49, 'Maisey', '1955-03-24', 'mpirouet1c@ehow.com');
insert into MOCK_DATA (id, name, birthday, email) values (50, 'Humbert', '1976-05-08', 'hwheeldon1d@networksolutions.com');
insert into MOCK_DATA (id, name, birthday, email) values (51, 'Miriam', '1964-07-02', 'mbearcock1e@amazon.com');
insert into MOCK_DATA (id, name, birthday, email) values (52, 'Eleonore', '1957-01-25', 'eclee1f@canalblog.com');
insert into MOCK_DATA (id, name, birthday, email) values (53, 'Chrystel', '1946-04-02', 'cdurbin1g@discuz.net');
insert into MOCK_DATA (id, name, birthday, email) values (54, 'Emiline', '1941-12-03', 'etaggert1h@virginia.edu');
insert into MOCK_DATA (id, name, birthday, email) values (55, 'Avery', '1972-08-17', 'aaspling1i@unc.edu');
insert into MOCK_DATA (id, name, birthday, email) values (56, 'Kori', '1971-02-22', 'kbenck1j@facebook.com');
insert into MOCK_DATA (id, name, birthday, email) values (57, 'Demetri', '1956-11-20', 'dcapitano1k@bloomberg.com');
insert into MOCK_DATA (id, name, birthday, email) values (58, 'Andie', '1930-01-01', 'adauber1l@sogou.com');
insert into MOCK_DATA (id, name, birthday, email) values (59, 'Brigg', '1930-10-01', 'bseager1m@pbs.org');
insert into MOCK_DATA (id, name, birthday, email) values (60, 'Ripley', '1938-12-26', 'rcrockley1n@webnode.com');
insert into MOCK_DATA (id, name, birthday, email) values (61, 'Sascha', '1957-11-08', 'scoldwell1o@admin.ch');
insert into MOCK_DATA (id, name, birthday, email) values (62, 'Joyce', '1934-07-14', 'jruppeli1p@senate.gov');
insert into MOCK_DATA (id, name, birthday, email) values (63, 'Ira', '1936-02-14', 'imazonowicz1q@google.ca');
insert into MOCK_DATA (id, name, birthday, email) values (64, 'Emmerich', '1988-03-06', 'eimeson1r@chronoengine.com');
insert into MOCK_DATA (id, name, birthday, email) values (65, 'Giralda', '1989-08-02', 'gfairholme1s@istockphoto.com');
insert into MOCK_DATA (id, name, birthday, email) values (66, 'Minna', '1980-02-24', 'mdunbavin1t@addtoany.com');
insert into MOCK_DATA (id, name, birthday, email) values (67, 'Reece', '1921-06-05', 'rjore1u@meetup.com');
insert into MOCK_DATA (id, name, birthday, email) values (68, 'Lucilia', '1990-07-03', 'lkayley1v@china.com.cn');
insert into MOCK_DATA (id, name, birthday, email) values (69, 'Darice', '1926-01-20', 'djosephoff1w@moonfruit.com');
insert into MOCK_DATA (id, name, birthday, email) values (70, 'Karly', '1986-10-04', 'ksavary1x@cmu.edu');
insert into MOCK_DATA (id, name, birthday, email) values (71, 'Fawnia', '1934-11-17', 'ftwells1y@soundcloud.com');
insert into MOCK_DATA (id, name, birthday, email) values (72, 'Hobart', '1934-09-17', 'hjean1z@sciencedaily.com');
insert into MOCK_DATA (id, name, birthday, email) values (73, 'Karoly', '1946-11-16', 'ksoles20@ning.com');
insert into MOCK_DATA (id, name, birthday, email) values (74, 'Xymenes', '1974-08-25', 'xreedick21@boston.com');
insert into MOCK_DATA (id, name, birthday, email) values (75, 'Laurel', '1972-12-17', 'lbrimilcombe22@liveinternet.ru');
insert into MOCK_DATA (id, name, birthday, email) values (76, 'Hollyanne', '1989-09-09', 'hhatterslay23@xing.com');
insert into MOCK_DATA (id, name, birthday, email) values (77, 'Brena', '1920-12-19', 'brarity24@hao123.com');
insert into MOCK_DATA (id, name, birthday, email) values (78, 'Damien', '1920-10-14', 'dposner25@pinterest.com');
insert into MOCK_DATA (id, name, birthday, email) values (79, 'Rutledge', '1998-07-27', 'rplomer26@symantec.com');
insert into MOCK_DATA (id, name, birthday, email) values (80, 'Shelley', '1951-01-20', 'sitzkovsky27@vk.com');
insert into MOCK_DATA (id, name, birthday, email) values (81, 'Solomon', '1946-08-22', 'spaszak28@hc360.com');
insert into MOCK_DATA (id, name, birthday, email) values (82, 'Ingamar', '1979-08-08', 'inewland29@networkadvertising.org');
insert into MOCK_DATA (id, name, birthday, email) values (83, 'Hedi', '1969-01-22', 'heathorne2a@cmu.edu');
insert into MOCK_DATA (id, name, birthday, email) values (84, 'Savina', '1992-10-23', 'starquini2b@clickbank.net');
insert into MOCK_DATA (id, name, birthday, email) values (85, 'Yul', '1973-08-05', 'yhedgeman2c@bloglovin.com');
insert into MOCK_DATA (id, name, birthday, email) values (86, 'Alyssa', '1931-08-09', 'amival2d@bloglines.com');
insert into MOCK_DATA (id, name, birthday, email) values (87, 'Fransisco', '1961-07-13', 'fgrint2e@hhs.gov');
insert into MOCK_DATA (id, name, birthday, email) values (88, 'Mallissa', '1979-10-11', 'mgiraudoux2f@photobucket.com');
insert into MOCK_DATA (id, name, birthday, email) values (89, 'Elbertine', '1929-03-03', 'estead2g@sun.com');
insert into MOCK_DATA (id, name, birthday, email) values (90, 'Rivi', '1934-11-02', 'rpaull2h@scribd.com');
insert into MOCK_DATA (id, name, birthday, email) values (91, 'Barty', '1923-06-25', 'bbrewer2i@sbwire.com');
insert into MOCK_DATA (id, name, birthday, email) values (92, 'Ivar', '1922-02-24', 'imishaw2j@globo.com');
insert into MOCK_DATA (id, name, birthday, email) values (93, 'Clemente', '1990-01-10', 'cmccaughran2k@comcast.net');
insert into MOCK_DATA (id, name, birthday, email) values (94, 'Rudyard', '1931-08-30', 'rmcpake2l@imageshack.us');
insert into MOCK_DATA (id, name, birthday, email) values (95, 'Theresa', '1939-02-12', 'tcolmer2m@businessinsider.com');
insert into MOCK_DATA (id, name, birthday, email) values (96, 'Olivero', '1976-02-06', 'ogreenhouse2n@vk.com');
insert into MOCK_DATA (id, name, birthday, email) values (97, 'Hastings', '1950-04-25', 'hmaulden2o@xrea.com');
insert into MOCK_DATA (id, name, birthday, email) values (98, 'Lyndel', '1920-10-26', 'ldeegin2p@gravatar.com');
insert into MOCK_DATA (id, name, birthday, email) values (99, 'Adrianne', '1951-09-15', 'afowlie2q@ezinearticles.com');
insert into MOCK_DATA (id, name, birthday, email) values (100, 'Deborah', '1965-04-14', 'dstraughan2r@hao123.com');

3)  Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.

// İsim (name) sütununu güncellemek:

UPDATE employee
SET name = 'John Doe'
WHERE name = 'Coob';


// Doğum günü (birthday) sütununu güncellemek:

UPDATE employee
SET birthday = '1990-06-15'
WHERE email = 'yserckd@home.pl';


// E-posta (email) sütununu güncellemek:

UPDATE employee
SET email = 'johndoe@example.com'
WHERE birthday = '1950/04/10';


// İsim ve doğum günü sütunlarını güncellemek:

UPDATE employee
SET name = 'Jane Smith',
    birthday = '1985-03-20'
WHERE id = 4;


// Tüm sütunları güncellemek:

UPDATE employee
SET name = 'Robert Johnson',
    birthday = '1978-12-10',
    email = 'robertjohnson@example.com'
WHERE id = 5;

4) Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.

DELETE FROM employee
WHERE id = 44;

DELETE FROM employee
WHERE name ='Constantin';

DELETE FROM employee
WHERE name = 'Jane Smith' AND birthday = '1985-03-20';

DELETE FROM employee
WHERE email = 'umallinsonn@hp.com';

DELETE FROM employee
WHERE id >5
RETURNING *;

THis is my first git commit















