
```sql
#zad.1.1
# Stworzenie tabel
create table uczestnicy like wikingowie.uczestnicy;
create table etapy_wyprawy like wikingowie.etapy_wyprawy;
create table sektor like wikingowie.sektor;
create table wyprawa like wikingowie.wyprawa;
# Dodanie rekordów
insert into uczestnicy select * from wikingowie.uczestnicy;
insert into etapy_wyprawy select * from wikingowie.etapy_wyprawy;
insert into sektor select * from wikingowie.sektor;
insert into wyprawa select * from wikingowie.wyprawa;


#zad.1.2
select k.nazwa from kreatura k left join uczestnicy u on u.id_uczestnika=k.idKreatury where id_uczestnika is null


#zad.1.3
select w.nazwa, sum(k.udzwig) from uczestnicy u inner join wyprawa w on u.id_wyprawy=w.id_wyprawy inner join kreatura k on u.id_uczestnika=k.idKreatury group by w.nazwa;

#zad.2.1
select w.nazwa, count(k.idKreatury) as 'liczbaUczestnikow', group_concat(k.nazwa) as 'uczestnicy' from uczestnicy u inner join wyprawa w on u.id_wyprawy=w.id_wyprawy inner join kreatura k on u.id_uczestnika=k.idKreatury group by w.nazwa;

#zad.2.2
select ew.idwyprawy, ew.dziennik, s.nazwa as 'nazwa_sektora', k.nazwa as 'nazwa_kierownika' from etapy_wyprawy ew inner join sektor s on ew.sektor=s.id_sektora inner join wyprawa w on ew.idwyprawy=w.id_wyprawy inner join kreatura k on w.kierownik=k.idKreatury order by w.data_rozpoczecia asc, ew.kolejnosc asc;

#zad.3.1
select s.nazwa, count(ew.sektor) from sektor s left join etapy_wyprawy ew on s.id_sektora = ew.sektor group by s.id_sektora

#zad.3.2
select k.nazwa, if(count(u.id_uczestnika) > 0, 'brał udział w wyprawie', 'nie brał udział w wyprawie') czy_bral_udzial from kreatura k left join uczestnicy u on u.id_uczestnika = k.idKreatury group by k.idKreatury;

#zad.4.1
select w.nazwa, sum(length(ew.dziennik)) as suma_znakow from etapy_wyprawy ew inner join wyprawa w on w.id_wyprawy = ew.idWyprawy group by w.nazwa having suma_znakow < 400;

#zad.4.2
select u.id_wyprawy, w.nazwa, sum(e.ilosc*z.waga) / count(distinct u.id_uczestnika) from uczestnicy u inner join ekwipunek e on u.id_uczestnika = e.idKreatury inner join zasob z on z.idZasobu = e.idZasobu inner join wyprawa w on w.id_wyprawy = u.id_wyprawy group by w.id_wyprawy;

#zad.5.1
select k.nazwa, datediff(w.data_rozpoczecia, k.dataUr) from kreatura k inner join wyprawa w on k.idKreatury = w.kierownik inner join etapy_wyprawy ew on ew.idWyprawy = w.id_wyprawy inner join sektor s on s.id_sektora = ew.sektor where s.nazwa = 'Chatka dziadka';

select rodzaj,
group_concat(nazwa separator '')
from kreatura group by;
```
