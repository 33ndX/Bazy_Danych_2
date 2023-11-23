```sql
zad.1.1

select * from postac
where nazwa <> 'Bjorn'
and rodzaj = 'wiking'
order by data_urasc limit 2

delete from postac where rodzaj='wiking' and nazwa!='Bjorn' and order by data_urasc limit 2;

#zad.1.2

alter table walizka
drop foreign key walizka_ibfk_2;

alter table przetwory
drop foreign key przetwory_ibfk_1;

alter table przetwory
drop foreign key przetwory_ibfk_2;

alter table postac change id_postaci id_postaci int;
#lub
alter table postac modify id_postaci int;

#zad.2.1
ALTER TABLE postac
DROP PRIMARY KEY;

alter table postac add column psesel char(11) primary key first;

update postac set pesel='64536748739' + id_postaci;

#-------------------------------------------------------------
select * from postac;

select nazwa from postac
where nazwa like '%a%';

selecet nazwa form postac
where nazwa regexp'^[aeuioy]'; #'[0-9]{2}-[0-9]{3}'

#-------------------------------------------------------------

#zad.3.1
update postac set nazwa_statku='SMS Schleswig-Holstein'
where nazwa like '%a%';

#zad.3.2
update statek set max_ladownosc=max_ladownosc * 0.7
where year(data_wodowania) between 1901 and 2000;

#zad.3.3
alter table postac add check(wiek < 1000);


#zad.4.1
alter table postac modify rodzaj  enum('wiking', 'ptak', 'kobieta','syrena', 'wąż');

insert into postac values('64536748323', '9','Loko', 'syrena', '2000-12-30', '23', NULL, NULL);

#zad.4.2
create table marynarz like postac;

#zad.4.3
alter table marynarz add foreign key (id_postaci) references postac(id_postaci);


#zad.5.1
update postac set nazwa_statku = null;

#zad.5.2
delete from postac where rodzaj='wiking' and nazwa='Diego';

#zad.5.3
delete from statek;

#zad.5.4
alter table postac
drop foreign key postac_ibfk_1;

drop table statek;

#zad.5.5
insert into zwierz  select id_postaci, nazwa, wiek from postac where rodzaj = 'ptak' or rodzaj = 'wąż';


 


```
