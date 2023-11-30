# Zadanie 1



```sql
create table kreatura select * from wikingowie.kreatura;
 create table zasob select * from wikingowie.zasob;
 create table ekwipunek select * from wikingowie.ekwipunek;
select * from zasob;
select * from zasob where rodzaj = 'jedzenie';
select idZasobu , ilosc from ekwipunek where idKreatury in(1,3,5);


```

# zadanie 2 

```sql
 select * from kreatura where not rodzaj = 'wiedzma' and udzwig > 50;
 select * from zasob where waga between 2 and 5;
 select * from kreatura where nazwa like '%or%' and udzwig between 30 and 70;

```



# Zadanie 3

```sql

 select * from zasob where dataPozyskania like '____-08-__' union
 select * from zasob where dataPozyskania like '____-07-__';
 select * from kreatura where dataUr is not null order by dataUr asc;
select * from zasob where rodzaj is not null order by waga asc;



```
# Zadanie 4


```sql
--1
select distinct ilosc, rodzaj from zasob where rodzaj = 'jedzenie' and ilosc = 1;
--2
 select concat(nazwa , ' oto ', rodzaj) from kreatura where rodzaj like 'wi%' and rodzaj is not
null;
--3
 select waga * ilosc from zasob where dataPozyskania between '2000-01-01' and '2007-12-31';    


```

# Zadanie 5


```sql
--2
 select * from zasob where not(rodzaj is not null);
--3
 select distinct nazwa, rodzaj from zasob where nazwa like 'Ba%' union select distinct nazwa, rodzaj from zasob where nazwa like '%os';





```








