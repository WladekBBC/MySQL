# Zadanie 1
```sql
 select imie , nazwisko, data_urodzenia from pracownik;
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
