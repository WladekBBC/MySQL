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
