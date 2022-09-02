# View Sql Server db deadlock

La query estrae i deadlock dalla sessione standard sql server (db --> Gestione --> Eventi estesi --> Sessioni --> system_health). Si ricorda che system health non conserva i dati per molto tempo (circa una settimana).
Si può lancaire la query anche su altre sessioni create ad hoc per il monitoraggio.

~~~
SELECT XEvent.query('(event/dataivalue/deadlock)[1]') AS DeadlockGraph
FROM ( 
SELECT XEvent.query('.') AS XEvent 
FROM ( 
SELECT CAST(target_data AS XML) AS TargetData 
FROM sys.dm_xe_session_targets st 
INNER JOIN sys.dm_xe_sessions s ON s.address = st.event_session_address 
WHERE s.NAME = 'system_health' 
AND st.target_name = 'ring_buffer'
)AS Data 
CROSS APPLY TargetData.nodes('RingBufferTarget/event[@name="xml_deadlock_report"]') AS XEventData(XEvent) 
)AS source; 
~~~
