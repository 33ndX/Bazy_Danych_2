## **Zadanie lab04**

Teskt **pogrubiony** lub _kursywa_

**Zadanie, pkt1**
```sql

SELECT * FROM osoba;

#zad.1
create table postac ( id_postaci int auto_increment primary key,
 nazwa varchar(40),
 rodzaj enum('wiking','ptak','kobieta'),
data_ur date,
wiek int unsigned);

#zad.2
CREATE TABLE walizka(id_walizki int auto_increment primary key,
 pojemnosc int unsigned, kolor enum('rozowy','czerwony','teczowy','zolty'),
 id_wlasciciela int, forgei CREATE TABLE walizka(id_walizki int auto_increment primary key,
 pojemnosc int unsigned, kolor enum('rozowy','czerwony','teczowy','zolty'),
 id_wlasciciela int,
forgein key(id_wlasciciela)
references postac(id_postaci) on delete key(id_wlasciciela)
references postac(id_postaci) on delete cascade
);

#zad.2.1
alter table walizka alter kolor set default 'rozowy';

#zad.2.2
insert into walizka values(default,50,default,3);

#zad.3.1
create table izba (
adres_budynku varchar(50) not null,
nazwa_izby varchar(50) not null,
metraz mediumint unsigned,
wlasciciel int,
primary key(adres_budynku, nazwa_izby)
foreign key (wlasciciel)
references postac(id_postaci) on delete set null
);
#zad.3.2
alter table izba add column
kolor varchar(30) default 'czarny'
after metraz;

#zad.3.3
insert into izba values
('Kolejowa 23', 'spiżarnia', 10, default,1);
select * from izba

#zad.4.1
create table przetwory(
id_przetworu int auto_increment primary key,
rok_prodkucji smallint default 1654,
id_wykonawcy int,
zawartosc varchar(30),
dodatek varchar(30) default'papryczka chilli',
id_konsumenta int,
foreign key (id_wykonawcy)
references postac(id_postaci),
foreign key (id_konsumenta)
references postac(id_postaci) 
);

#zad.4.2
insert into przetwory values(default, default, 1, 'bigos', default, 2);

#zad.5.1
insert into postac values(default, 'Olaf', 'wiking', '1700-11-22', 323),
(default, 'Jan', 'wiking', '1700-10-25', 323),
(default, 'Diego', 'wiking', '1700-11-12', 323),
(default, 'Gorn', 'wiking', '1700-12-30', 323),
(default, 'Lee', 'wiking', '1700-12-21', 323);

#zad.5.2
create table statek (
nazwa_statku varchar(50) primary key,
rodzaj_statku enum('pancernik', 'niszczyciel', 'krazownik', 'fregata'),
data_wodowania date,
max_ladownosc mediumint unsigned
);

#zad.5.3
insert into statek values('SMS Schleswig-Holstein', 1,'1906-12-17', 750),
('Bismarck', 1, '1939-02-14', 2500);

#zad.5.4
Alter table postac add funkcja varchar(30);

#zad.5.5
update postac
set funkcja = 'kapitan'
where nazwa = 'Bjorn';

#zad.5.6
alter table postac add nazwa_statku varchar(30);

alter table postac add
foreign key(nazwa_statku)
references statek(nazwa_statku);




```

Polecenie `SELECT` służy do wybieraniu danych z bazy.

lista ponumerowana 
1. Punkt 1.
2. Punkt 2.  
2.1 Punkt

listy wypunktowane:
* punkt 1
* punkt2
  * punkt2.1
 
    
