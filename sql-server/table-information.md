# View Fk and Table Information

Il comando 
~~~
EXEC sp_fkeys  'TableName'
~~~
ritorna le informazioni riguardanti le chiavi esterne.

Il comando come scritto sopra può trarre in inganno perché prende in ingresso il parametro pktable_name (equivale a: EXEC sp_fkeys @pktable_name = 'TableName') , cioè il nome della tabella della chiave primaria, mostrando dove la tabella è referenziata.

Per ottenere invece le fk della tabella indicata bisogna eseguire: 
~~~
EXEC sp_fkeys @fktable_name= 'TableName'
~~~
Per altre informazioni vedere http://infocenter.sybase.com/help/index.jsp?topic=/com.sybase.dc36273_1251/html/sprocs/X38671.htm .

Un comando più intuitivo è invece: 
~~~
EXEC sp_help 'TableName' 
~~~
che mostra tutte le informazioni della tabella comprese chiavi esterne ed eventuali tabelle dove la tabella indicata è referenziata. 

Se la tabella è referenziata tra le altre informazioni del risultanti ci sarà la sezione "Table is referenced by foreign key", altrimenti la sezione non sarà presente.
