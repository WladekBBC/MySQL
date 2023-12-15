# LABO 5
# Zadanie 1
***Punkt A***
usuwamy dwoch wikingów z tabeli postac
```sql
select * from postac;
select * from postac where rodzaj = 'wiking' and nazwa <> 'Bjorn' order by data_ur asc limit 2;
delete from postac where rodzaj = 'wiking' and nazwa <> 'Bjorn' order by data_ur asc limit 2;
```
***Punkt B***

```sql
alter table postac change id_postaci id_postaic int ;
alter table postac drop primary key;
alter table postac change id_postaci id_postaci int ;
alter table postac modify postac_statek int;
alter table walizka1 drop foreign key walizka1_ibfk_1;
alter table postac drop foreign key postac_ibfk_1;
alter table przetwory drop foreign key przetwory_ibfk_1;
alter table przetwory drop foreign key przetwory_ibfk_2;

```



# Zadanie 2

***Podpunkt A***
```sql
alter table postac add column pesel char(11) primary key first;
alter table postac add primary key (pesel);
update postac set pesel='1208392391' + id_postaci;
select * from postac;
```

***podpunkt b***
```sql
alter table postac modify rodzaj enum('wiking', 'ptak', 'kobieta', 'syrena');
```


***podpunkt c***
```sql
insert into postac(nazwa, rodzaj, wiek) values('Gertruda Nieszczera', 'syrena', '111');
```
# Zadanie 3

***PODPUNKT a***
```sql 
select nazwa from postac where nazwa like '%a%';
select nazwa from postac where nazwa like '__-___';
select nazwa from postac where nazwa regexp '^d';
```
***podpunkt b***
```sql
select * from statek where data_wodowania between '1900-01-01' 
and '2000-12-31';
set max_ladownosc = max_ladownoscmax_ladownosc * 0.7 where data_wodowania between '1900-01-01' and 
'200-12-31';
```
***podpunkt c***
```sql
alter table postac add check (wiek<=1000);
```
# Zadanie 4

***podpunkt a***
 ```sql
 alter table postac modify rodzaj enum('wiking', 'ptak', 'kobieta', 'syrena','waz');
```
***podpunkt b***
```sql
create table marynarz like postac;
desc marynarz;
create table marynarz like postac;
desc marynarz;
insert into marynarz select * from postac where statek is not null;
```

***podpunkt c***
```sql
desc marynarz;
select * from marynarz;
alter table marynarz add primary key (pesel);
alter table marynarz add column marynarz_statek varchar(60);
alter table marynarz add foreign key(marynarz_statek) references statek(nazwa_statku);
```

# Zadanie 5
```sql
update marynarz set marynarz_statek = null;
alter table marynarz drop foreign key marynarz_ibfk_1;
drop table statek;

```

