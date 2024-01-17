# Zadanie 1

```sql
 SELECT AVG(p.pensja),MIN(p.pensja),
  MAX(p.pensja), d.nazwa 
	FROM pracownik p JOIN dzial d 
	ON d.id_dzialu = p.dzial GROUP BY d.nazwa;


```

# Zadanie 2

```sql
 SELECT k.pelna_nazwa, 
	SUM(pz.ilosc * pz.cena) AS wartosc FROM 
	klient k JOIN zamowienie z 
	ON k.id_klienta = z.klient JOIN
	pozycja_zamowienia pz ON
	z.id_zamowienia = pz.zamowienie
	GROUP BY  pz.zamowienie, k.pelna_nazwa
	ORDER BY  wartosc DESC LIMIT 10
;

```
