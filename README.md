### Tecnologie lato client

- **HTML (Hypertext Markup Language)** -  è il linguaggio di markup utilizzato per strutturare e definire il contenuto delle pagine web. Costituisce la base per creare il layout e la struttura dell'interfaccia utente.
- **CSS (Cascading Style Sheets**) - sono utilizzati per definire la presentazione e lo stile delle pagine web. Consente agli sviluppatori di controllare i colori, i caratteri, il layout e altri aspetti visivi dell'interfaccia utente.
- **JavaScript** - è un linguaggio di scripting che permette l'interattività in applicazioni web. Viene utilizzato per creare elementi dell'interfaccia utente dinamici e reattivi, gestire le interazioni con l'utente ed eseguire convalide lato client
- **Cookie e memorizzazione locale** - sono meccanismi lato client per memorizzare piccole quantità di dati nel browser dell'utente. Sono spesso utilizzati per la gestione delle sessioni e per ricordare le preferenze dell'utente

---

### Tecnologie lato server

- **Server Web** - Il server Web è responsabile della ricezione e della risposta alle richieste HTTP dei client (browser Web). Ospita i file dell'applicazione web, elabora le richieste e invia le risposte ai client. (Apache2, Nginx, Microsoft IIS ecc.)
- **Application Server** - L'application server esegue la logica aziendale
dell'applicazione web. Elabora le richieste degli utenti, accede ai database ed esegue calcoli per generare contenuti dinamici che il server web può servire ai client.
- **Server di database** - Il server di database memorizza e gestisce i dati
dell'applicazione web. Memorizza le informazioni sugli utenti, i contenuti, le configurazioni e altri dati rilevanti necessari per il funzionamento dell'applicazione. (MySQL, PostgreSQL, MSSQL, Oracle ecc.)
- **Linguaggi di scripting lato server** - I linguaggi di scripting lato server (ad esempio, PHP, Python, Java, Ruby) sono utilizzati per gestire l'elaborazione lato server. Interagiscono con i database, eseguono convalide e generano contenuti dinamici prima di inviarli al client.

---

### Comunicazione e flusso di dati

- Le applicazioni Web comunicano su Internet utilizzando il protocollo HTTP (Hypertext Transfer Protocol).
- Quando un utente interagisce con l'applicazione web facendo clic sui collegamenti o inviando moduli, il client invia richieste HTTP al server.
- Il server elabora queste richieste, interagisce con il database se necessario, esegue le azioni richieste e genera una risposta HTTP.
- La risposta viene quindi rinviata al client, che esegue il rendering del contenuto e lo presenta all'utente

### Interscambio di dati

- L'interscambio di dati si riferisce al processo di scambio di dati tra diversi sistemi o applicazioni informatiche, consentendo loro di comunicare e condividere informazioni.
- È un aspetto fondamentale dell'informatica moderna, che consente
l'interoperabilità e la condivisione dei dati tra sistemi, piattaforme e tecnologie diverse.
- L'interscambio di dati comporta la conversione dei dati da un formato ad un altro. un altro, rendendolo compatibile con il sistema ricevente.
- In questo modo si garantisce che i dati possano essere interpretati e utilizzati correttamente dal destinatario, indipendentemente dalle differenze nelle strutture di dati, nei linguaggi di programmazione o nei sistemi operativi.

### Tecnologie di interscambio dati

- API (Application Programming Interfaces) - Le API consentono a diversi sistemi software di interagire e scambiare dati. Le applicazioni Web utilizzano le API per integrarsi con servizi esterni, condividere dati e fornire funzionalità ad altre applicazioni.

### Protocolli di interscambio dati

- JSON (JavaScript Object Notation) - JSON è un formato di interscambio dati leggero e ampiamente utilizzato, facile da leggere e scrivere sia per gli esseri umani che per le macchine. Si basa sulla sintassi di JavaScript ed è utilizzato principalmente per la trasmissione di dati tra un server e un'applicazione web come alternativa a XML.
- XML (eXtensible Markup Language) - XML è un formato versatile per lo scambio di dati che utilizza tag per definire la struttura dei dati. Consente agli utenti di creare tag personalizzati e di definire complesse strutture gerarchiche di dati. L'XML è comunemente usato per i file di configurazione, i servizi Web e lo scambio di dati tra
sistemi diversi.
- REST (Representational State Transfer) - REST è uno stile architettonico del software che utilizza metodi HTTP standard (GET, POST, PUT, DELETE) per lo scambio di dati. È ampiamente utilizzato per creare API web che consentono alle applicazioni di interagire e scambiare dati su Internet.
- SOAP (Simple Object Access Protocol) - SOAP è un protocollo per lo scambio di informazioni strutturate nella realizzazione di servizi Web. Utilizza XML come formato di interscambio dei dati e fornisce un metodo standardizzato per la comunicazione tra sistemi diversi.

### Tecnologie di sicurezza

- Meccanismi di autenticazione e autorizzazione - L'autenticazione verifica l'identità degli utenti, mentre l'autorizzazione controlla l'accesso alle diverse parti dell'applicazione web in base ai ruoli e ai permessi degli utenti.
- Crittografia (SSL/TLS) - SSL (Secure Socket Layer) o TLS (Transport Layer Security) viene utilizzato per crittografare i dati trasmessi tra il client e il server, garantendo una comunicazione sicura e la protezione dei dati.

### Tecnologie esterne

- Reti di distribuzione dei contenuti (CDN) - Le CDN sono utilizzate per distribuire contenuti statici (ad esempio, immagini, file CSS, librerie JavaScript) a più server situati in tutto il mondo, migliorando le prestazioni e l'affidabilità dell'applicazione web
- Librerie e framework di terze parti - Le applicazioni Web spesso sfruttano librerie e framework di terze parti per accelerare lo sviluppo e accedere a funzionalità avanzate.

###Architettura delle applicazioni web

![image](https://github.com/user-attachments/assets/7cc74f32-507c-49bf-97fc-034ef9058297)

###Come vengono renderizzate le pagine web

![image](https://github.com/user-attachments/assets/8586dc9b-ba44-4aad-b229-f1388e7f0ae8)

###Come i browser web analizzano le risposte

![image](https://github.com/user-attachments/assets/8ae20ba3-7073-4e97-8838-fdcdd9e40784)



