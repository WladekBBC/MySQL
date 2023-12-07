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
```
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

```

# Zadanie 4

```sql
--1
select * from kreatura natural join ekwipunek;
--2


```
