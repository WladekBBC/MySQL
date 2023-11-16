# Zadanie cicha woda
***Punkt A***
usuwamy dwoch wikingów z tabeli postac
```sql
select * from postac;
select * from postac where rodzaj = 'wiking' and nazwa <> 'Bjorn' order by data_ur asc limit 2;
delete from postac where rodzaj = 'wiking' and nazwa <> 'Bjorn' order by data_ur asc limit 2;
```
***Punkt B***
pierwsza część
```sql
alter table postac change id_postaci id_postaic int ;

```
