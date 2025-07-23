# Rebuild sequences

di seguito il comando per fare il riallineamento delle sequenze DB (colonne autoincrement)  (es. dopo un porting dati).
Lo script di seguito stampa solamente tutti i comandi:
```
DECLARE
     n integer;
     CURSOR C IS SELECT table_name, column_name FROM USER_tab_columns WHERE identity_column = 'YES' AND TABLE_NAME NOT LIKE '%GTT%'
                    and table_name in (select table_name from user_tables);
 BEGIN
     FOR R IN C LOOP
         execute immediate 'select nvl(max('||r.column_name||'),0)+1 from PRISMADB.'||r.table_name into n;
         --dbms_output.put_line('table = ' || r.table_name || ' - col ' || r.column_name || ' - conta ' || n || '\n');
         dbms_output.put_line('ALTER TABLE SCHEMA_NAME.'||R.TABLE_NAME||' MODIFY '||R.COLUMN_NAME||' GENERATED ALWAYS AS IDENTITY START WITH '||to_char(n)||' INCREMENT BY 1 NOMAXVALUE;');
    END LOOP;
END;
```

Mentre lo script di seguito esegue al volo:
```
 DECLARE
     n integer;
     CURSOR C IS SELECT table_name, column_name FROM USER_tab_columns WHERE identity_column = 'YES' AND TABLE_NAME NOT LIKE '%GTT%'
                    and table_name in (select table_name from user_tables);
 BEGIN
     FOR R IN C LOOP
         execute immediate 'select nvl(max('||r.column_name||'),0)+1 from PRISMADB.'||r.table_name into n;
         dbms_output.put_line('table = ' || r.table_name || ' - col ' || r.column_name || ' - conta ' || n || '\n');
         EXECUTE IMMEDIATE 'ALTER TABLE SCHEMA_NAME.'||R.TABLE_NAME||' MODIFY '||R.COLUMN_NAME||' GENERATED ALWAYS AS IDENTITY START WITH '||to_char(n)||' INCREMENT BY 1 NOMAXVALUE';
    END LOOP;
END;
/
```
