# Zadanie 1
```sql
--1
select avg(waga) as srednia_waga from kreatura where rodzaj = 'wiking';

--2
select avg(waga), count(nazwa) from kreatura group by rodzaj;

--3
select avg(2023 -  year(dataUr)), rodzaj from kreatura where year(dataUr) > 999 group by rodzaj;

```


# Zadanie 2
```sql
--3
 select count(distinct nazwa) from zasob where ilosc > 1;
--1
 select rodzaj, sum(waga * ilosc) as suma_wag from zasob group by rodzaj;
--2
 select avg(waga) from zasob where ilosc >= 4 group by nazwa having sum(waga) > 10;

```


# Zadanie 3
```sql
--3
select nazwa, idKreatury from kreatura where idKreatury not in (select distinct idKreatury from ekwipunek where idKreatury is not null);
--2
select k.nazwa, e.idZasobu, z.nazwa, e.ilosc from kreatura k inner join ekwipunek e on k.idKreatury = e.idKreatury inner join zasob z on e.idZasobu = z.idZasobu;
--1
select k.nazwa, e.ilosc from kreatura k inner join ekwipunek e on k.idKreatury = e.idKreatury;

```

# Zadanie 4

```sql
--1
select * from kreatura natural join ekwipunek;
--2
select k.nazwa as nazwa_kreatury, k.dataUr,
-> z.rodzaj from kreatura k join ekwipunek e on
-> k.idKreatury = e.idKreatury join zasob z on
-> e.idZasobu = z.idZasobu where z.rodzaj is not null and
-> k.dataUr is not null order by k.dataUr asc limit 5;
--3
select k1.idKreatury, k1.nazwa as nazwa_kreatury_1,
-> k2.idKreatury,  k2.nazwa as nazwa_kreatury_2
-> from kreatura k1 join kreatura k2 on
-> k1.idKreatury = k2.idKreatury - 5 where k2.idKreatury is not null;

```
# Zadanie 5 


```sql
--1
  select distinct (k.rodzaj) as rodzaj_kreatury,
-> e.ilosc, avg(z.waga * e.ilosc) as sreadnia_waga from kreatura k
-> inner join ekwipunek e on k.idKreatury = e.idZasobu
-> inner join zasob z on z.idZasobu = idEkwipunku
-> where k.rodzaj not in('waz','malpa') and
-> e.ilosc < 30 group by k.rodzaj, e.ilosc;



```
