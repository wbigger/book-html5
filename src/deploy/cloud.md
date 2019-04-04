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

## Gestori Cloud
Il panorama dei gestori Cloud, come si può immaginare, è molto variegato e dinamico. Esistono comunque alcune grandi aziende che in questo momento gestiscono la maggior parte degli utenti:
- [Amazon Web Service](http://aws.amazon.com/)
- [Google Cloud Platform](https://cloud.google.com/)
- [Microsoft Azure Platform](https://azure.microsoft.com/)
- [Alibaba Cloud](https://us.alibabacloud.com/)

In Italia abbiamo [Aruba Cloud](https://www.cloud.it/), che fornisce servizi con particolare attenzione al rispetto delle normative europee.

## Amazon Web Services
Noi utilizzeremo i servizi di Amazon Web Services (abbreviato: AWS), perché è uno dei gestori più utlizzati e grazie da una convenzione, abbiamo del credito gratuito per gli studenti della nostra scuola.

Per cominciare, chiedete al docente di invitarvi ad AWS Educate, e seguite le indicazioni che vi arrivano via email.

Una volta completata la registrazione. Aprire AWS Educate.
Lanciare un'istanza su AWS. Accedere via terminale.
```
sudo yum update -y

sudo yum install docker -y
sudo usermod -aG docker $USER # logout per avere effetto
sudo systemctl start docker
sudo curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version

sudo yum install git -y
```
Uscire con ctrl-D e rientrare per fare in modo che tutte le modifiche abbiano effetto.

A questo punto la nostra istanza è pronta per il deploy. Seguite le istruzioni sul deployment locale [quando saranno disponibili], che riassumo di seguito. Ricordatevi di sostituire l'URL del repository con il vostro.
```
# Siamo sull'istanza remota
git clone <URL-del-vostro-repository-su-github>
cd <cartella-del-progetto-appena-scaricata>
docker-compose up
```
Fatto!

Riferimenti:
- [Docker](https://hackernoon.com/running-docker-on-aws-ec2-83a14b780c56)
- [Docker compose](https://docs.docker.com/compose/install/)
