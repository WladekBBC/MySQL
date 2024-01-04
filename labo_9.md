# LABO 9

# Zadanie 1
```sql

DELIMITER //
CREATE TRIGGER before_insert_update_kreatura
BEFORE INSERT ON kreatura
FOR EACH ROW
BEGIN
    IF NEW.waga <= 0 THEN
        SET NEW.waga = 1;
    END IF;
END;
//
DELIMITER ;

```
# Zadanie 2


```sql
 CREATE TABLE archiwum_wypraw LIKE wyprawa;
 DESC archiwum_wypraw;
 ALTER TABLE archiwum_wypraw
 MODIFY COLUMN kierownik VARCHAR(1000);
 DELIMITER //
 CREATE TRIGGER wyprawa_przed_usunienciem
 BEFORE DELETE ON wyprawa
 FOR EACH ROW
 BEGIN
     INSERT INTO archiwum_wypraw (id_wyprawy, nazwa,
     data_rozpoczecia, data_zakonczenia, kierownik)
     SELECT w.id_wyprawy, w.nazwa, w.data_rozpoczecia, w.data_zakonczenia, k.nazwa
     FROM wyprawa w
     JOIN kreatura k ON k.idKreatury = w.kierownik
     WHERE id_wyprawy = OLD.id_wyprawy;
 END;
 //
 DELIMITER ;
```

# Zadanie 3

```sql
DELIMITER //
CREATE PROCEDURE eliksir_sily(IN id INT)
BEGIN
    UPDATE kreatura
    SET udzwig = 1.2 * udzwig
    WHERE idKreatury = id;
END;
//
DELIMITER ;
```



# Zadanie 4

```sql
DELIMITER //

CREATE TRIGGER uczestnicy_after_insert
AFTER INSERT ON uczestnicy
FOR EACH ROW
BEGIN
	DECLARE tesciowa varchar(100);
	DECLARE sektor_id integer;
	DECLARE czy_tesciowa bool;
	DECLARE czy_chata_dziadka bool;
	SET tesciowa = 'Tesciowa';
	SET sektor_id = 7;
	
/** sprawdzanie czy tesciowa bierze udział w wyprawie **/
    
IF tesciowa in (
	SELECT nazwa from kreatura WHERE idKreatury in 
	( SELECT id_uczestnika from uczestnicy where id_wyprawy=NEW.id_wyprawy)) 
	
THEN 
    
	SET czy_tesciowa = true;
	END IF;
    
IF sektor_id in (
	SELECT sektor FROM etapy_wyprawy WHERE idWyprawy=NEW.id_wyprawy
	) 
THEN 
	SET czy_chata_dziadka = true;
END IF;
    
IF czy_tesciowa AND czy_chata_dziadka
    
THEN  
	INSERT INTO system_alarmowy VALUES(default,'Tesciowa nadchodzi',default);
END IF;

END
//

DELIMITER ;

```
