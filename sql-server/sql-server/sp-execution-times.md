# Stored procedure execution times

~~~
--Tempistiche StoredProcedures
SELECT  d.object_id, d.database_id, OBJECT_NAME(object_id, database_id) 'proc name',   
    d.cached_time, d.last_execution_time, d.total_elapsed_time/1000000 as total_elapsed_time,  
    d.total_elapsed_time/d.execution_count/1000000 AS [avg_elapsed_time],  
    d.last_elapsed_time/1000000 as last_elapsed_time, d.execution_count  
FROM sys.dm_exec_procedure_stats AS d  
ORDER BY last_elapsed_time DESC;
~~~
