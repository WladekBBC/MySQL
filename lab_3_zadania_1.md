# Zadanie 1
```sql
 SELECT imie , nazwisko, data_urodzenia FROM pracownik;
```

# Zadanie 2

```sql

  SELECT imie , nazwisko,
	ROUND((DATEDIFF(CURDATE(), data_urodzenia))/365, 1)
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
