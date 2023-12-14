# Zadanie 1

```sql
--1

 CREATE TABLE uczestnicy AS SELECT * FROM wikingowie.etapy_wyprawy;
 CREATE TABLE uczestnicy AS SELECT * FROM wikingowie.uczestnicy;
 CREATE TABLE uczestnicy AS SELECT * FROM wikingowie.sektor;
 CREATE TABLE uczestnicy AS SELECT * FROM wikingowie.wyprawa;

--2

 SELECT nazwa, idKreatury FROM kreatura
	WHERE idKreatury NOT IN (SELECT DISTINCT id_uczestnika
	FROM uczestnicy WHERE id_wyprawy IS NOT NULL);

--3


```



# Zadanie 2

```sql
--1

 SELECT rodzaj , COUNT(*), 
  	GROUP_CONCAT(nazwa SEPARATOR ' | ')
  	AS nazwy FROM kreatura GROUP BY rodzaj;




```
