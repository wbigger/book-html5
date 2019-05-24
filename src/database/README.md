# NoSQL database

I database NoSQL sono un'alternativa ai database SQL particolarmente utilizzata per le applicazioni web.

Caratteristiche:
- non hanno uno schema che definisce la struttura del database
- alcuni dati sono ripetuti in diverse parti del database per migliorare le performance di lettura (a scapito di quelle di scrittura e spazio utilizzato)
- hanno una struttura ad albero e non a tabelle
- non esistono chiavi primarie esplicite, ma solo per convenzione dello sviluppatore
- non si interrogano con SQL, ma con altri metodi, tipicamente Restful (vedi dopo)

Vantaggi:
- più semplice modificare i campi dei database, utile se i requisiti cambiano continuamente
- può scalare orizzontalmente, ovvero può essere distribuito facilmente su più computer

Svantaggi:
- la lettura dei campi deve essere molto difensiva perché non si hanno certezze sulla struttura dei dati ricevuti

Link utili:
- [REST](https://it.wikipedia.org/wiki/Representational_State_Transfer), una filosofia di scrittura delle API per la quale al centro di tutto c'è la risorsa che viene manipolata attraverso vari metodi. Molto spesso associata all'HTTP. Con REST si possono effettuare le operazioni CRUD per un database, in [questo link](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete) potete vedere una tabella di confronto tra NoSQL e SQL.
- [Guida di Firebase](https://firebase.google.com/docs/database/rest/structure-data) su come strutturare i dati, rende molto bene operativamente cosa significa programmare per un database NoSQL
- [Video di confronto](https://www.youtube.com/watch?v=v_hR4K4auoQ&t=593s) tra SQL e NoSQL.
- [Pagina di confronto](https://www.sitepoint.com/sql-vs-nosql-differences/) tra SQL e NoSQL.

# Frameworks
Quando si vogliono gestire funzionalità complesse come sincronizzazione dello stato locale della pagina con il database remoto, lavoro offline, etc., può essere molto utile usare un _framework_ che permetta di gestire queste cose in modo più semplice.

Attualmente (giugno 2019) tra i framework più usati ci sono:
- [Angular](https://angular.io/), mantenuto da Google, usa TypeScript
- [React](https://en.wikipedia.org/wiki/React_(JavaScript_library)), mantenuto da Facebook (per l'esattezza è una libreria) e utilizza i concetti di stateful, properties e Virtual DOM
- [Flutter](https://flutter.dev/), anche questo mantenuto da Google, è l'ultimo nato ma sta riscuotendo un enorme successo. Basato sul linguaggio Dart.
