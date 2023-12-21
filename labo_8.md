# Zadanie 1

```sql
--1

 CREATE TABLE etapy_wyprawy AS SELECT * FROM wikingowie.etapy_wyprawy;
 CREATE TABLE uczestnicy AS SELECT * FROM wikingowie.uczestnicy;
 CREATE TABLE sektor AS SELECT * FROM wikingowie.sektor;
 CREATE TABLE wyprawa AS SELECT * FROM wikingowie.wyprawa;

--2

 SELECT nazwa, idKreatury FROM kreatura 
	WHERE idKreatury NOT IN (SELECT DISTINCT id_uczestnika
	FROM uczestnicy WHERE id_wyprawy IS NOT NULL);
 
--3
 SELECT w.nazwa AS nazwa_wyprawy, SUM(e.ilosc) AS niesione_rzeczy
	FROM kreatura k JOIN ekwipunek e 
	ON k.idKreatury = e.idKreatury JOIN uczestnicy u 
	ON k.idKreatury = u.id_uczestnika JOIN wyprawa w 
	ON u.id_wyprawy = w.id_wyprawy GROUP BY w.nazwa;

```



# Zadanie 2

```sql
--1
 
 SELECT w.nazwa, COUNT(u.id_uczestnika) 
	AS liczba_uczestnikow, 
	GROUP_CONCAT(k.nazwa SEPARATOR ' - ') 
	AS uczestnicy FROM wyprawa w 
	JOIN uczestnicy u ON w.id_wyprawy = u.id_wyprawy
	JOIN kreatura k ON k.idKreatury = u.id_uczestnika
	GROUP BY w.nazwa;

--2

SELECT k.nazwa, w.nazwa, s.nazwa 
	AS nazwa_sektora, e.idEtapu 
	FROM etapy_wyprawy e
	JOIN sektor s ON e.sektor = s.id_sektora
	JOIN wyprawa w ON e.idWyprawy = w.id_wyprawy
	JOIN kreatura k ON w.kierownik = k.idKreatury
	ORDER BY w.data_rozpoczecia AND e.kolejnosc;


```

# Zadanie 3
```sql
--1
 SELECT s.nazwa , count(ew.sektor)
	FROM sektor s 
	LEFT JOIN etapy_wyprawy ew 
	ON s.id_sektora = ew.sektor
	GROUP BY s.nazwa;

--2
 SELECT k.nazwa,
	IF(count(u.id_uczestnika)> 0 , 'brał udział', 'nie brał udziału')
	AS czy_uczestniczyl
 	FROM uczestnicy u 
	RIGHT JOIN kreatura k 
	ON k.idKreatury = u.id_uczestnika
	GROUP BY k.nazwa;

```

# Zadanie 4

```sql
--1
 SELECT w.nazwa, sum(length(ew.dziennik)) 
	AS suma_znaczkow
	FROM etapy_wyprawy ew JOIN wyprawa w 
	ON w.id_wyprawy = ew.idWyprawy  
	GROUP BY w.nazwa HAVING suma_znaczkow < 400;


```












