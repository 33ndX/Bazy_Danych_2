## **Zadanie lab04**

Teskt **pogrubiony** lub _kursywa_

**Zadanie, pkt1**
```sql

SELECT * FROM osoba;
zad.1
create table postac ( id_postaci int auto_increment primary key, nazwa varchar(40), rodzaj enum('wiking','ptak','kobieta'), data_ur date, wiek int unsigned);

zad.2
CREATE TABLE walizka(id_walizki int auto_increment primary key, pojemnosc int unsigned, kolor enum('rozowy','czerwony','teczowy','zolty'), id_wlasciciela int, forgei CREATE TABLE walizka(id_walizki int auto_increment primary key, pojemnosc int unsigned, kolor enum('rozowy','czerwony','teczowy','zolty'), id_wlasciciela int, forgein key(id_wlasciciela) references postac(id_postaci) on deleten key(id_wlasciciela) references postac(id_postaci) on delete cascade);
zad.2.1
alter table walizka alter kolor set default 'rozowy';
2.2
insert into walizka values(default,50,default,3);



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
 
    
