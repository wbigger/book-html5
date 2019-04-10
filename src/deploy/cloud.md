# Cloud computing
Un'azienda invece di dislocare le proprie risorse e servizi su una macchina all'interno dei locali dell'azienda stessa, può scegliere di dislocarli su macchine non di sua proprietà posizionate da qualche parte nel mondo in dei locali insieme ad altre decine, centinaia o migliaia di macchine che servono anche altre aziende. Questi locali vengono chiamate _server-farm_ o _data center_. Per farvi un'idea, potete guardare [il tour virtuale](https://www.youtube.com/watch?v=XZmGGAbHqa0) dei data center di Google.

Negli ultimi anni, c'è stato un forte trend nello spostamento dei servizi da un'infrastuttura on-premises verso il cloud. Questo per diversi motivi:
- non dover gestire una infrastruttura interna, con relativo personale
- possibilità di pagare solo i servizi usati, senza costi iniziali
- rischi di perdita dati o interruzione di servizio molto bassi
- maggiore sicurezza dagli attacchi informatici

Tutto questo è reso possibile anche dalla diffusione capillare della fibra ottica in molte città del mondo.

Alcuni svantaggi invece sono legati all privacy: i dati sono fisicamente ospitati su qualche server remoto, con minor controllo sull'accesso ai dati da terze parti. Alcune leggi europee limitano l'utilizzo del cloud per alcune categorie di enti pubblici e privati, per esempio richiedendo che i data center siano risiedano sul territorio della comunità europea (in altre parole, non si possono usare data center in USA o Cina).

> Anche per uso personale il cloud ormai è estremamente diffuso: pensate ad esempio a Dropbox, Google Drive, Google Docs, la web mail e servizi analoghi. Sono tutte applicazioni che conservano e gestiscono file ed informazioni in cloud.

## Emissioni e sostenibilità
Con l'aumentare dell'uso del cloud, i data center sono aumentati di numero e di dimensioni, e la loro gestione è diventata un problema anche dal punto di vista ambientale. Alcune [stime di Nature](https://www.nature.com/articles/d41586-018-06610-y) prevedono che nel 2030 le attività legate al networking ed Internet arriveranno al 20% del consumo dotale di energia elettrica, con i data center con la percentuale maggiore.

> Una parte significativa del traffico è generato da video virali, magari di pochi secondi o minuti. Pensate anche all'ambiente quando condividete sui social!


## Gestori Cloud
Il panorama dei gestori Cloud, come si può immaginare, è molto variegato e dinamico. Esistono comunque alcune grandi aziende che in questo momento gestiscono la maggior parte degli utenti:
- [Amazon Web Service](http://aws.amazon.com/)
- [Google Cloud Platform](https://cloud.google.com/)
- [Microsoft Azure Platform](https://azure.microsoft.com/)
- [Alibaba Cloud](https://us.alibabacloud.com/)

In Italia abbiamo [Aruba Cloud](https://www.cloud.it/), che fornisce servizi con particolare attenzione al rispetto delle normative europee.

## Amazon Web Services
Noi utilizzeremo i servizi di Amazon Web Services (abbreviato: AWS), perché è uno dei gestori più utlizzati e grazie da una convenzione, abbiamo del credito gratuito per gli studenti della nostra scuola.

### Creazione account
Per cominciare, chiedete al docente di invitarvi ad AWS Educate, e seguite le indicazioni che vi arrivano via email.

Nel form di registrazione mettete i seguenti dati:
- Institute: Marconi Civitavecchia
- Level: Graduate
- Graduation Date: il mese (nel futuro) in cui prevedete di diplomarvi

Una volta completata la registrazione, aprire AWS Educate e fare il login.

### Creare un'istanza
Dopo aver fatto il login, nella pagina che vi si presenta selezionare "Go to Classroom" e quindi la propria classe.

Dopo un paio di click si dovrebbe aprire una pagina di Vocareum, dove potete vedere il vostro credito residuo. Cliccate sul bottone AWS Console.

Ora vi ritrovate in una console reale di AWS! Ricordatevi di rimanere sempre in Virginia Settetrionale, altrimenti il vostro credito _non_ funzionerà.

Dalla lista dei servizi in alto, selezionate EC2. Nella pagina che si apre, selezionate il bottone blu per lanciare una nuova istanza. Lasciate tutto di default: Linux Amazon 2 AMI su x86 a 64bit, e t2.micro.

Generate una nuova chiave privata quando richiesto. **ATTENZIONE!** mettete la chiave privata in un luogo sicuro, per esempio inviatevela per posta o copiatela su una chiavetta. Se perdete il file, non potrete più accedere alla vostra istanza; se qualcuno entra in possesso del file, potrà entrare e modificare la vostra istanza cloud.

### Accedere ad un'istanza
Una volta lanciata l'istanza, andate nella lista delle istanze, premete su "Connect", lasciate il default "A standalone SSH client". Come SSH Client, Amazon (e anche io) per Windows consiglia [Git Bash](https://git-scm.com/downloads), che avete già installato. PuTTY è supportato ma più difficile da configurare e far funzionare. Seguite le indicazioni per accedere e finalmente vi troverete dentro la vostra macchina remota!

### Configurazione della macchina remota
Queste operazioni vanno fatto solo la prima volta.

Dal terminale sulla macchina remota, lanciate i seguenti comandi.
```
sudo yum update -y

# install docker and docker-compose
sudo yum install docker -y
sudo groupadd docker
sudo usermod -aG docker $USER # logout per avere effetto
sudo systemctl start docker
sudo curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version

# install git
sudo yum install git -y
```
Uscire con ctrl-D e rientrare per fare in modo che tutte le modifiche abbiano effetto.

Ora ci manca un ultimo passo per poter accedere da remoto alla nostra macchina: aprire la porta http.

>
> Riferimenti:
> - [Docker](https://hackernoon.com/running-docker-on-aws-ec2-83a14b780c56)
> - [Docker compose](https://docs.docker.com/compose/install/)

### Gruppi di sicurezza
Di default, l'unica porta aperta su un'istanza appena creata è la 22 per la connessione SSH. Se vogliamo poter accedere via browser, ci serve aprire anche le porte per l'accesso HTTP. Anche queste operazioni vanno fatte una sola volta per ogni istanza.

Andare sulla lista delle istanze, scorrere a destra finché non si arriva alla colonna "Security Group" e selezionare il link "launch-wizard-1". Nella finestra che si apre cliccare sul bottone "Actions"->"Edit inbound rules" e quindi "Add rule". Selezionare come tipo "HTTP" e come valore della porta mettete quella del vostro sito. Per sapere il numero di porta esatto, consultate il vostro file docker-compose.yml: è quel numero che va da 8080 a 8089.

### Deploy
A questo punto la nostra istanza è pronta per il deploy. Le istruzioni sono le stesse del deployment locale, che riassumo di seguito. Ricordatevi di sostituire l'URL del repository con il vostro.

```
# we are on the remote instance
git clone <URL-del-vostro-repository-su-github>
cd <cartella-del-progetto-appena-scaricata>
docker-compose up
```
Fatto, la macchina è pronta!

### Accesso alla pagina web
Ora siamo pronti per accedere alla pagina web della nostra istanza dal browser. Tornate sulla lista delle istanze e nei dettagli sotto, copiate il "Public DNS" e copiatelo sul vostro browser. Ricordatevi di aggiungere la porta. Il link risultante dovrebbe essere una cosa di questo genere:

```
ec2-18-215-229-80.compute-1.amazonaws.com:8080
```

Se tutto va bene, vedrete la vostra pagina in cloud. Complimenti!

### Fermare l'istanza
Dopo che avrete fatto le vostre prove, ricordatevi di fermare l'istanza: infatti per il semplice fatto che è _running_, state consumando credito, indipendentemente dagli accessi.

Per fermare l'istanza, andate sulla lista delle istanze, selezionate "Actions", quindi su "States" selezionate "Stop" se volete fermarla e prevedete di riutilizzarla in seguito, o "Terminate" se volete completamente eliminarla.

Precisazione: in generale, anche quando una istanza è _stopped_, continuate a consumare de credito per lo _storage_ che state utilizzando. Ma nel nostro caso la quantità di storage utilizzata è minima e quindi anche questa componente del costo.
