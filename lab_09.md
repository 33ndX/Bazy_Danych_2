```sql

#zad.1.1
alter table kreatura modify waga int default 0;

DELIMITER //
create trigger kreatura_before_insert
before insert on kreatura
for each row 
begin 
	if new.waga <= 0 
    then
    set new.waga = 1;
    end if;
end
//

zad.2.1 dokonczyc
DELIMITER //
create trigger wyprawy_before_delete
insert into archiwum_wypraw
select w.id_wyprawy, w.nazwa, w.data_rozpoczecia, w.data_zakonczenia, k.nazwa
from wyprawa w  inner join kreatura k on w. kierownik=k.idKreatury
where id.wyprawy=old.id_wyprawy
//
zad.3.1


```
