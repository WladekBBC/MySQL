# LABO 9

# Zadanie 1
```sql

DELIMITER //
CREATE TRIGGER before_insert_update_kreatura
BEFORE INSERT OR UPDATE ON kreatura
FOR EACH ROW
BEGIN
    IF NEW.waga <= 0 THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'Waga kreatury musi być większa od zera.';
    END IF;
END;
//
DELIMITER ;
```
