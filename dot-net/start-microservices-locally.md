# How to start .net microservices locally in Visual Studio debug


Come startare:

- posizionarsi da prompt dei comandi nella cartella del progetto che si vuole startare

- lanciare il comando dotnet run

- aprire una powershell e lanciare:

  Get-Process -Id (Get-NetTCPConnection -LocalPort numeroPorta).OwningProcess  (mettere al posto di numeroPorta la porta definita nel progetto).

  Questo servirà a capire quale è il pid del processo da startare per agganciarlo al debug di visual studio.

- per debbugare: andare su visual studio come amministratore. 

- andare su DEBUG --> CONNETTI A PROCESSO 

- cercare il processo attraverso il pid tovato in precedenza e connetterlo. 
