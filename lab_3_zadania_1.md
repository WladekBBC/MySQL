# Zadanie 1
```sql
 SELECT imie , nazwisko, data_urodzenia FROM pracownik;
```

# Zadanie 2

```sql

  SELECT imie , nazwisko,
	(YEAR(CURRDATE()) - YEAR(data_urodzenia))
	AS wiek FROM pracownik;
```

# Zadanie 3
```sql
SELECT DISTINCT(d.nazwa), d.id_dzialu, COUNT(p.id_pracownika) 
	AS ilosc_pracownikow FROM dzial d 
	JOIN pracownik p ON p.dzial = d.id_dzialu
	GROUP BY d.nazwa, d.id_dzialu;

```

# Zadanie 4 

```sql
 SELECT DISTINCT k.nazwa_kategori,
	t.kategoria, SUM(s.ilosc) AS ilosc_towaru
	FROM kategoria k JOIN towar t
	ON k.id_kategori = t.kategoria
	JOIN stan_magazynowy s ON 
	t.id_towaru = s.towar
	GROUP BY k.nazwa_kategori, t.kategoria;
```

# Zadanie 5 

```sql

 SELECT k.nazwa_kategori,
	GROUP_CONCAT(t.nazwa_towaru) AS cos
	FROM kategoria k JOIN towar t
	ON t.kategoria = k.id_kategori
	GROUP BY k.id_kategori
```

# Zadanie 6

```sql
	
 SELECT ROUND(AVG(pensja), 2) FROM pracownik;

```
# Zadanie 7

```sql

 SELECT ROUND(AVG(pensja), 2)
	FROM pracownik WHERE data_zatrudnienia < 				SUBDATE(data_zatrudnienia, interval 5 year);

```

# Zadanie 8

```sql

-- liczenie ogolnych zamowien
select t.nazwa_towaru, p.towar, sum(p.ilosc) as suma
from towar t
join pozycja_zamowienia p on t.id_towaru = p.towar
group by p.towar
order by suma desc limit 10;

-- liczenie ilosci unikalnych zamowien
select t.nazwa_towaru, p.towar, count(*) suma
from towar t
join pozycja_zamowienia p on t.id_towaru=p.towar
group by p.towar
order by suma desc limit 10;

```
# Zadanie 9

```sql
select z.numer_zamowienia, sum(p.ilosc*p.cena),
z.id_zamowienia from zamowienie z
join pozycja_zamowienia p on z.id_zamowienia=p.zamowienie
where year(z.data_zamowienia)=2017
and quarter(z.data_zamowienia) = 1
group by z.id_zamowienia;

```

# Zadanie 10


```sql
select pr.imie, pr.nazwisko, sum(p.ilosc*p.cena)
suma from zamowienie z
join pozycja_zamowienia p on z.id_zamowienia=p.zamowienie
join pracownik pr on pr.id_pracownika=z.pracownik_id_pracownika
group by pr.id_pracownika order by suma desc;

```
