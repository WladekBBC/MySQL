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
	ON k.idKreatury=e.idKreatury JOIN uczestnicy u 
	ON k.idKreatury=u.id_uczestnika JOIN wyprawa w 
	ON u.id_wyprawy=w.id_wyprawy GROUP BY w.nazwa;

```



# Zadanie 2

```sql
--1

 SELECT rodzaj , COUNT(*), 
  	GROUP_CONCAT(nazwa SEPARATOR ' | ')
  	AS nazwy FROM kreatura GROUP BY rodzaj;




```
