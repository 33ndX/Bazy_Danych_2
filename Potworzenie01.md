```sql
#zad.1

select imie, nazwisko, year(data_urodzenia) from pracownik;

#zad.2

select imie, nazwisko, (year(now()) - year(data_urodzenia)) as wiek from pracownik;

#zad.3

select d.nazwa, count(p.id_pracownika) from dzial d 
inner join pracownik p on d.id_dzialu = p.dzial 
group by d.nazwa;

#zad.4

select k.nazwa_kategori, count(t.nazwa_towaru) as liczba_produktow
from kategoria k inner join towar t on 
k.id_kategori = t.kategoria group by k.nazwa_kategori;

#zad.5

select k.nazwa_kategori, group_concat(t.nazwa_towaru) 
from kategoria k inner join towar t on 
k.id_kategori = t.kategoria group by k.nazwa_kategori;
#zad.6

select round(avg(pensja), 1) from pracownik;

#zad.7

select round(avg(pensja), 2) from pracownik
where data_zatrudnienia <= '2019-01-11';
select data_zatrudnienia, subdate(data_zatrudnienia, interval 5 year)
from pracownik;

#zad.8

select t.nazwa_towaru, p.towar, sum(p.ilosc) as suma from towar t inner join 
pozycja_zamowienia p on t.id_towaru=p.towar group by p.towar
order by suma desc limit 10;

#zad.9

select z.id_zamowienia, z.numer_zamowienia, 
sum(pz.ilosc*pz.cena)
from zamowienie z inner join pozycja_zamowienia pz
on z.id_zamowienia=pz.zamowienie
where quarter(z.data_zamowienia)=1
and year(z.data_zamowienia)=2017
group by z.id_zamowienia;

#zad.10

select pr.imie, pr.nazwisko, 
sum(pz.ilosc*pz.cena) as wartosc
from zamowienie z inner join pozycja_zamowienia pz
on z.id_zamowienia=pz.zamowienie
inner join pracownik pr on pr.id_pracownika=z.pracownik_id_pracownika 
group by pr.id_pracownika order by wartosc desc;
```
