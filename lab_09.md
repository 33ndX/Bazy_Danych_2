```sql

#zad.1.1
alter table kreatura modify waga int default 0;

DELIMITER //
create trigger kreatura_before_insert
before insert ON kreatura
for each row
BEGIN
	IF NEW.waga <= 0
    THEN
		SET NEW.waga = 1;
	END IF;
END
//

DELIMITER //
create trigger kreatura_before_update
before update ON kreatura
for each row
BEGIN
	IF NEW.waga <= 0
    THEN
		SET NEW.waga = 1;
	END IF;
END
//

show create trigger nazwa;

#zad.2.1 

create ... like ...
... modify ... varchar(50)

DELIMITER //
create trigger wyprawa_before_delete
before delete ON wyprawa 
for each row
BEGIN
	insert into archiwum_wypraw 
	select w.id_wyprawy, w.nazwa, w.data_rozpoczecia, w.data_zakonczenia, k.nazwa from wyprawa w
	inner join kreatura k on w.kierownik=k.idKreatury where id.wyprawy = old.id_wyprawy;
END
//
DELIMITER ;

#zad.3.1

DELIMITER $$
CREATE PROCEDURE eliksir_sily(IN id int)
BEGIN
Update kreatura set udzwig = 1.2 * udzwig where id_kreatury = id;
END
$$
DELIMITER ;

call eliksir_sily(1);

#zad.3.2

DELIMITER $$
CREATE PROCEDURE wieksze_litery(IN wprowadzony_tekst varchar(50))
BEGIN
select upper(wprowadzony_tekst);
END
$$
DELIMITER ;

call wieksze_litery('Test, test');

#zad.4.1

create table system_alarmowy(id_alarmu int, wiadomosc varchar(50));

#zad.4.2

CREATE TRIGGER uczestnicy_after_insert
AFTER INSERT ON uczestnicy
FOR EACH ROW
BEGIN
	DECLARE tesciowa varchar(100);
	DECLARE sektor_id integer;
	DECLARE czy_tesciowa bool;
	DECLARE czy_chata_dziadka bool;
	SET tesciowa = 'Tesciowa';
	SET sektor_id = 7;



IF tesciowa in (
	SELECT nazwa from kreatura WHERE idKreatury in 
	( SELECT id_uczestnika from uczestnicy where id_wyprawy=NEW.id_wyprawy)) 
	
THEN 
    
	SET czy_tesciowa = true;
	END IF;
    
IF sektor_id in (
	SELECT sektor FROM etapy_wyprawy WHERE idWyprawy=NEW.id_wyprawy
	) 
THEN 
	SET czy_chata_dziadka = true;
END IF;
    
IF czy_tesciowa AND czy_chata_dziadka
    
THEN  
	INSERT INTO system_alarmowy VALUES(default,'Tesciowa nadchodzi !!!');
END IF;

END
$$

DELIMITER ;


```
