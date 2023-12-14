
```sql
#zad.1.1
create table ekwipunek like wikingowie.ekwipunek;
create table kreatura like wikingowie.kreatura;
create table zasob like wikingowie.zasob;

insert into ekwipunek select * from wikingowie.ekwipunek;
insert into kreatura select * from wikingowie.kreatura;
insert into zasob select * from wikingowie.zasob;

#zad.1.2
SELECT * FROM zasob;

#zad.1.3
SELECT * FROM zasob WHERE typ='jedzenie';

#zad.1.4
SELECT idZasobu, ilosc
FROM kreatury
WHERE id IN (1, 3, 5);

#zad.2.1
SELECT *
FROM kreatura
WHERE rodzaj != 'wiedźma' AND udzwig >= 50;

#zad.2.2
SELECT *
FROM zasob
WHERE waga BETWEEN 2 AND 5;

#zad.2.3
SELECT *
FROM kreatura
WHERE nazwa LIKE '%or%' AND udzwig BETWEEN 30 AND 70;

#zad.3.1
SELECT *
FROM zasob
WHERE MONTH(dataPozyskania) IN (7, 8);

#zad.3.2
SELECT *
FROM zasob
ORDER BY rodzaj ASC, waga ASC;

#zad.3.3
SELECT *
FROM kreatura
ORDER BY dataUr DESC
LIMIT 5;

#zad.4.1
select distinct rodzaj from kreatura;

#zad.4.2
SELECT CONCAT(nazwa, ' - ', rodzaj) AS nazwa_i_rodzaj
FROM kreatura
WHERE rodzaj LIKE 'wi%';

#zad.4.3
SELECT nazwa, ilosc * waga AS całkowita_waga
FROM zasob
WHERE YEAR(dataPozyskania) BETWEEN 2000 AND 2007;

#zad.5.1
SELECT waga*0.7 as wagaNetto, waga*0.3 as wagaOdpadkow  FROM zasob;

#zad.5.2
SELECT * FROM zasob where rodzaj is null;

#zad.5.3
SELECT distinct rodzaj,nazwa FROM zasob where nazwa like 'Ba%' or nazwa like '%os' order by nazwa asc;
```
