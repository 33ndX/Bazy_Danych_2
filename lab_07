```sql

#zad.1.1
select avg(waga) from kreatura where rodzaj = 'wiking';

#zad.1.2
select rodzaj, avg(waga), count(waga) from kreatura group by rodzaj;

#zad.1.3
select avg(year(now()) - year(dataUr)) as wiek from kreatura;


#zad.2.1
select rodzaj, sum(waga*ilosc) as suma_wag from zasob group by rodzaj;
Podpunkt b)

#zad.2.2
select nazwa, avg(waga)  from zasob where ilosc>=4 group by nazwa having sum(waga) > 10;

#zad.2.3
select rodzaj, count(distinct nazwa) as liczba from zasob where ilosc > 1 group by rodzaj having liczba > 1;

#zad.3.1
select nazwa,ilosc from kreatura, ekwipunek where kreatura.idKreatury=ekwipunek.idKreatury;
#lub inner join
select k.nazwa,e.ilosc from kreatura k inner join ekwipunek e on k.idKreatury=e.idKreatury;

#zad.3.2
select k.nazwa, e.idZasobu, z.nazwa, e.ilosc from kreatura k inner join ekwipunek e on k.idKreatury=e.idKreatury inner join zasob z on z.idZasobu=e.idZasobu;

#zad.3.3
select * from kreatura k left join ekwipunek e on k.idKreatury=e.idKreatury where e.idEkwipunku
is  null;

#podzapytanie
select idKreatury from kreatura where idKreatury not in (select distinct idKreatury from ekwipunek where idKreatury is not null)

#zad.4.1
select k.nazwa, z.nazwa, k.dataUr from kreatura k inner join ekwipunek e on k.idKreatury=e.idKreatury inner join zasob z on z.idZasobu=e.idZasobu having year(k.dataUr) like '167_';

#zad.4.2
select * from kreatura k inner join ekwipunek e on k.idKreatury=e.idKreatury inner join zasob z
on z.idZasobu=e.idZasobu where z.rodzaj = 'jedzenie' order by k.nazwa asc limit 5;

#zad.4.3
#połączenie tabeli samej ze soba
select concat(k1.nazwa,' ',k2.nazwa) from kreatura k1 inner join kreatura k2 where k1.idKreatury - k2.idKreatury = 5;


#zad.5.1
select k.rodzaj, avg(e.ilosc* z.waga) from kreatura k inner join ekwipunek e on e.idKreatury=k.idKreatury inner join zasob z on e.idZasobu=z.idZasobu where k.rodzaj not in ('malpa', 'waz') group by k.rodzaj having sum(e.ilosc) < 30;

#zad.5.2
select rodzaj, nazwa, min(year(dataUr)) as najmlodszaKreatura, max(year(dataUr)) as najstarszaKreatura from kreatura group by rodzaj


```
