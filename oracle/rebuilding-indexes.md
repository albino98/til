# Rebuilding indexes in unusable state

il seguente comando genera un ulteriore comando da lanciare per effettuare una rebuild degli indici in stato 'UNUSABLE':

~~~
SELECT 'ALTER INDEX '||OWNER||'.'||INDEX_NAME||' REBUILD;'
FROM DBA_INDEXES
WHERE STATUS = 'UNUSABLE';
~~~

Reference: https://dba.stackexchange.com/questions/3754/ora-01502-index-or-partition-of-such-index-is-in-usable-state-problem
