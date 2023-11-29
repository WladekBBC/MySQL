# BAZY DANYCH
# Zadanie 1 
```sql
 create table postac(
    -> id_postaci int  primary key auto_increment,
    -> nazwa varchar(40),
    -> rodzaj enum('wiking', 'ptak', 'kobieta'),
    -> data_ur date,
    -> wiek int unsigned);
Query OK, 0 rows affected (0.06 sec)

insert into postac(nazwa, rodzaj, data_ur, wiek)  values('Bjorn', 'wiking', '1999-01-01', '24');
insert into postac(nazwa, rodzaj, data_ur, wiek)  values('Drozd', 'wiking', '1899-01-01', '124');
insert into postac(nazwa, rodzaj, data_ur, wiek)  values('Tesciowa', 'kobieta', '1799-01-01', '224');
update postac set wiek = '88' where id_postaci = 3;
```
# Zadanie 2

```sql

create table walizka(id_walizki int primary key auto_increment,
->pojemnosc int unsigned,
-> kolor enum('rozowy', 'czerwony', 'teczowy', 'zolty'),
-> id_wlasciciela int,
-> foreign key (id_wlasciciela) references postac(id_postaci) on delete cascade);
Query OK, 0 rows affected (0.07 sec)

```


***ZADADNIE 4***
### punkt 1 i 2
```sql

CREATE TABLE przetwory(id_przetworu INT primary KEY auto_increment, 
rok_produkcji  smallint default '1654',
id_wykonawcy int default null,
id_konsumenta int default null ,
foreign key(id_wykonawcy) references postac(id_postaci) on delete set null,
zawartosc varchar(50),
dodatek varchar(50) default 'papryczka chilli',
foreign key(id_konsumenta) references postac(id_postaci) on delete set null
 );


INSERT INTO przetwory(zawartosc, dodatek) values('bigos','papryczka chilli');
```

***ZADANIE 5***
# punkt 1
dodajemy nowe postacie do tabeli postac
```SQL
INSERT INTO postac(nazwa, rodzaj, wiek) values('Bigos','wiking', '23');
INSERT INTO postac(nazwa, rodzaj, wiek) values('Antonio Montana','wiking', '69');
INSERT INTO postac(nazwa, rodzaj, wiek) values('Potężny Osioł','wiking', '13');


```
# punkt 2
tworzymy tabele statek 
```SQL
CREATE TABLE statek(nazwa_statku varchar(60) primary KEY auto_increment, 
rodzaj_statku enum('duzy', 'maly', 'wojskowy', 'wedkarski'),
data_wodowania date,
max_ladownosc mediumint unsigned
 );
```
# punkt 3
dodajemy statki do tabeli statek
```sql
 INSERT INTO statek values('SantMarry', 'wojskowy','1999-11-09','200');
 INSERT INTO statek values('Johny Sins', 'duzy','1939-01-01','2');
 INSERT INTO statek values('Grand', 'maly','2000-12-12','42');

```

# punkt 4
dodajemy kolumnę funkcja do tabeli postac
```
sql
alter table postac add column funkcja varchar(50);

```

# punkt 5
zmieniamy kolumnę funkcja dla Bjorna i wikingów
```sql
update postac set funkcja = 'kapitan' where id_postaci = 1;
update postac set funkcja = 'wiking' where id_postaci = 5;
update postac set funkcja = 'wiking' where id_postaci = 6;
update postac set funkcja = 'wiking' where id_postaci = 7;
```
# punkt 6
dodajemy klucz obcy dla relacji miedzy postacią a statkiem 
```sql
alter table postac add foreign key(postac_statek) references statek(nazwa_statku) on delete restrict;
```
# punkt 7
wsadzamy wikingów
```sql

update postac set postac_statek = 'SantMarry' where nazwa = 'Drozda';
update postac set postac_statek = 'Johny Sins' where nazwa = 'Bigos';
update postac set postac_statek = 'Grand' where nazwa = 'Tesciowa';

```


# punkt 8
usuwamy spizarnie z tabeli izba
```sql

delete from izba where nazwa_izby = 'spizarnia';

```

# punkt 9
usuwamy tabele izba
```sql

drop table izba ;

```














