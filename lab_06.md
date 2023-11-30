
```sql
#zad.1.1
CREATE TABLE kreatura AS
SELECT *
FROM wikingowie.kreatura;

CREATE TABLE ekwipunek AS
SELECT *
FROM wikingowie.ekwipunek;

CREATE TABLE zasob AS
SELECT *
FROM wikingowie.zasob;

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

#4.3
SELECT nazwa, ilosc * waga AS całkowita_waga
FROM zasob
WHERE YEAR(dataPozyskania) BETWEEN 2000 AND 2007;
```
