Eseguire con utenza dba o comunque con una utenza avente i privilegi necessari.

~~~
SELECT  LAST_DDL_TIME, TIMESTAMP
FROM    DBA_OBJECTS
WHERE   OBJECT_TYPE = 'PROCEDURE'
        AND OBJECT_NAME = 'PRC_MINE'
~~~

~~~
-- visualizza solo modifiche alle sp
SELECT    owner
,	  object_name
,	  last_ddl_time
FROM	  all_objects	-- or dba_objects, if you have privileges
WHERE	  object_type  IN ('PROCEDURE')
ORDER BY  last_ddl_time desc
;
~~~

~~~
-- visualizza modifiche a tutti gli oggetti e mostra il tipo di oggetti
SELECT    owner
,	  object_name
,	  last_ddl_time
, object_type
FROM	  all_objects	-- or dba_objects, if you have privileges
--WHERE	  object_type  IN ('TYPES')
ORDER BY  last_ddl_time desc
;
~~~



