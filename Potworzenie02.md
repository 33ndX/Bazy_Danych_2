``` sql
#zad.1

select dzial.nazwa, min(pracownik.pensja),max(pracownik.pensja),avg(pracownik.pensja) from pracownik
inner join dzial on id_dzialu = pracownik.dzial
group by nazwa;

#zad.2

select klient.pelna_nazwa, sum(ilosc * cena) as suma from klient
inner join zamowienie on id_klienta = zamowienie.klient
inner join pozycja_zamowienia on id_zamowienia = pozycja_zamowienia.zamowienie
group by id_klienta
order by suma desc limit 10;

#zad.3

select year(zamowienie.data_zamowienia)as rok,sum(ilosc * cena) as suma from zamowienie
inner join pozycja_zamowienia on id_zamowienia = pozycja_zamowienia.zamowienie
group by rok
order by suma desc;

#zad.4

select sum(ilosc * cena) as suma from pozycja_zamowienia
inner join zamowienie on id_zamowienia = zamowienie
inner join status_zamowienia on id_statusu_zamowienia = status_zamowienia
where nazwa_statusu_zamowienia = 'anulowane'
group by nazwa_statusu_zamowienia;

#zad.5

select  miejscowosc, count(zamowienie), sum(ilosc * cena) from zamowienie
inner join pozycja_zamowienia on id_zamowienia = pozycja_zamowienia.zamowienie
inner join klient on id_klienta = zamowienie.klient
inner join adres_klienta on id_klienta = adres_klienta.klient
where typ_adresu=1
group by miejscowosc;

#zad.6

select sum(pozycja_zamowienia.ilosc*pozycja_zamowienia.cena) as Przychod,sum(pozycja_zamowienia.ilosc*towar.cena_zakupu) as CenaZakupu,sum(pozycja_zamowienia.ilosc*pozycja_zamowienia.cena)-sum(pozycja_zamowienia.ilosc*towar.cena_zakupu) as Dochod from pozycja_zamowienia
inner join towar on towar = towar.id_towaru
inner join zamowienie on zamowienie = zamowienie.id_zamowienia
inner join status_zamowienia on id_statusu_zamowienia = status_zamowienia
where nazwa_statusu_zamowienia = 'zrealizowane'
group by nazwa_statusu_zamowienia;


#zad.7

select kategoria.nazwa_kategori,sum(stan_magazynowy.ilosc*towar.cena_zakupu) as wartosc_zakupu_magazynu,sum(stan_magazynowy.ilosc*pozycja_zamowienia.cena) as wartosc_przy_sprzedazy from kategoria
inner join towar on id_kategori = towar.kategoria
inner join stan_magazynowy on id_towaru = stan_magazynowy.towar
inner join pozycja_zamowienia on id_towaru = pozycja_zamowienia.towar
group by nazwa_kategori;


#zad.8

select year(zamowienie.data_zamowienia)as rok,sum(pozycja_zamowienia.ilosc * cena)as przychod,sum(pozycja_zamowienia.ilosc*towar.cena_zakupu)as cena_zakupu,(sum(pozycja_zamowienia.ilosc * cena))-sum(pozycja_zamowienia.ilosc*towar.cena_zakupu) as dochod from zamowienie
inner join pozycja_zamowienia on id_zamowienia = pozycja_zamowienia.zamowienie
inner join towar on id_towaru = pozycja_zamowienia.towar
group by rok

#zad.9

select monthname(pracownik.data_urodzenia) as miesiac, count(pracownik.id_pracownika) as liczba_pracownikow from pracownik
group by miesiac
order by FIELD(miesiac,'January', 'February', 'March', 'April', 'May', 'June', 
'July','August','September','October','November','December')

#zad.10

select pracownik.imie,pracownik.nazwisko,(TIMESTAMPDIFF(MONTH,data_zatrudnienia,date(now()))* pensja) as koszt from pracownik
where data_zatrudnienia  <= date(now())
group by id_pracownika;
```
