# Find db columns by data-type and length

~~~
 SELECT table_name [Table Name], column_name [Column Name]
FROM information_schema.columns where data_type = 'varchar' 
~~~

~~~
select 
    table_name as [Table Name]
  , column_name as [Column Name]
from information_schema.columns 
where data_type = 'varchar' 
  and character_maximum_length=2
~~~
