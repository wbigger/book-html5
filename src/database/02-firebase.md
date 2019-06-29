# Firebase

Per capire meglio come funzionano i database NoSQL, useremo Google Firebase.

Google Firebase è estremamente semplice da usare e molto potente. Per usarlo basta avere un account Google con Clout Platform attivato.

Andare sul sito di [Firebase](http://firebase.google.com/), quindi:
- accedere con il proprio account Google
- cliccare su "Vai alla console" in alto a destra
- cliccare su Add Project
- scegliere un nome per il database e lasciare tutto il resto di default, quindi premere su "Create project"
- nel progetto appena creato, andare nel menu a sinistra su "Database".

A questo punto dobbiamo fare una scelta. La versione del database consigliato oggi da Google è il nuovo Cloud Firestore, più potente ma richiede un minimo di pratica per cominciare. Noi possiamo usare la versione **Real-time Database**, che era la versione standard fino a poco tempo fa ma è comunque ancora supportata. Il vantaggio di quest'ultima versione è che è più immediata da usare.

Quando viene richiesto, selezionare le regole di test per l'accesso al database, in modo tale che in questo momento possiamo non preoccuparci dell'autenticazione dell'utente per le operazioni di lettura o scrittura.

Configurazione completata :)
