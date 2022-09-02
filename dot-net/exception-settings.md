# Stop debugger when exception occurs

Tramite il menù "debug --> windows --> exception settings" è possibile flaggare specifici tipi di eccezioni. Per le eccezioni impostate il debugger si fermerà
non appena si verificherà l'eccezione, nel blocco più interno.

Ad esempio, se si riceve un'eccezione KeyNotFoundException in un metodo senza try catch (o con un try catch esterno) dove è presente un for di lunga durata,
difficile da debuggare, flaggando il tipo di eccezione specifico, il debugger si fermerà all'interno del metodo esattamente durante l'iterazione che provoca
l'errore, dando la possibilità di vedere la chiave non trovata. Nel dettaglio, quindi:

-	andare su debug --> windows --> exception settings

-	spuntare la voce System.Collections.Generic e/o System.Collection.Generic.KeyNotFoundException

Riavviare e vedere la chiave ricercata nel punto dove si verifica l'eccezione.
