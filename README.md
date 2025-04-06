L'architettura delle applicazioni web si riferisce alla struttura e all' **organizzazione** dei **componenti** e delle **tecnologie utilizzate per costruire un'applicazione web.**

**Definisce** come le diverse **parti** dell'applicazione **interagiscono tra** **loro** per fornire le funzionalità, gestire le richieste degli utenti e gestire i dati

**Prima di eseguire una valutazione della sicurezza su un'applicazione Web, è necessario. È di vitale importanza sapere come funzionano le applicazioni web rispetto all'architettura sottostante. Questa conoscenza vi permetterà di capire molto meglio dove e come identificare e sfruttare potenziali vulnerabilità o configurazioni errate nelle applicazioni web.**

### Modello client-server

- **Cliente**: Il client rappresenta **l'interfaccia** **utente** e **l'interazione dell'utente** **con l'applicazione web**. È il **front-end** dell'applicazione a cui gli **utenti** **accedono** **attraverso** i loro **browser** web. Il client è **responsabile** della **visualizzazione** delle **pagine** web, della **gestione** degli **input** dell'utente e **dell'invio** di **richieste** al server per ottenere dati o azioni.
- **Server**: Il server rappresenta il **back-end** dell'applicazione web. **Elabora** le **richieste** del **client**, **esegue** **la logica** aziendale dell'applicazione, **comunica con** i **database** e altri servizi e **genera** le **risposte** da inviare **al client.**

  ![image](https://github.com/user-attachments/assets/a55a83f4-8fcd-4193-b0d1-cedfc738db20)

- **Interfaccia utente (UI):** L'interfaccia utente è la presentazione visiva dell'applicazione web vista e interagita dagli utenti. Comprende elementi pagine web, moduli, menu, pulsanti e altri componenti interattivi.
- **Tecnologie lato client:** Le tecnologie lato client, come HTML (Hypertext Markup Language), CSS (Cascading Style Sheets) e JavaScript, sono utilizzate per creare l'interfaccia utente e gestire le interazioni direttamente all'interno del browser web dell'utente.
- **Tecnologie lato server:**  Le tecnologie lato server, come i linguaggi di programmazione (ad esempio, PHP, Python, Java, Ruby) e i framework, sono utilizzate per implementare la logica aziendale dell'applicazione, elaborare le richieste dei client, accedere ai database e generare contenuti dinamici da inviare al client
- **Banche dati:**  I database sono utilizzati per memorizzare e gestire i dati dell'applicazione web. Memorizzano le informazioni sugli utenti, i contenuti, le configurazioni e altri dati rilevanti necessari per il funzionamento dell'applicazione.
- **Logica di applicazione:**  La logica dell'applicazione rappresenta le regole e le procedure che governano il funzionamento dell'applicazione web. Include l'autenticazione degli utenti, la convalida dei dati, i controlli di sicurezza e altre regole aziendali.
- **Server web:** I server Web gestiscono la richiesta iniziale dei client e servono i componenti lato client, come i file statici (HTML, CSS, JavaScript), agli utenti.
- **Server applicativi:** I server applicativi eseguono il codice lato server e gestiscono l'elaborazione dinamica delle richieste dei client. Comunicano con i database, eseguono la logica aziendale e generano contenuti dinamici.

### Elaborazione lato client

- L'elaborazione lato client **comporta** l'esecuzione di **attività** e **calcoli** s**ul dispositivo dell'utente**, in genere all'interno del suo browser web.
- Il lato client si riferisce al lato utente dell'applicazione web, dove risiedono il browser web e l'interfaccia utente.
- L'elaborazione lato client presenta alcune **limitazioni**. **Non** è **adatta** per la **gestione** di **operazioni sensibili** o critiche, in quanto può essere **facilmente manipolata** dagli utenti o **da** soggetti **malintenzionati**.

### Caratteristiche principali dell'elaborazione lato client

- **Interazione con l'utente**: L'elaborazione lato client è particolarmente indicata per le attività che interazione e un feedback immediati da parte dell'utente, in quanto non è necessario inviare i dati al server
- **Esperienza utente reattiva:** Poiché l'elaborazione avviene localmente, le operazioni sul lato client possono fornire un'esperienza utente più fluida e reattiva
- **JavaScript: J**avaScript è il principale linguaggio di programmazione utilizzato per i client.  elaborazione laterale. Permette agli sviluppatori di manipolare il contenuto della pagina web, gestire le interazioni con l'utente ed eseguire convalide senza coinvolgere il server
- **Convalida dei dati**: La convalida lato client assicura che l'input dell'utente soddisfi criteri specifici prima di essere inviato al server, riducendo la necessità di effettuare richieste inutili al server

### Elaborazione lato server

- L'elaborazione lato server comporta l'esecuzione di attività e calcoli sul server web, ovvero il computer remoto in cui è ospitata l'applicazione web.
- Il lato server si riferisce al backend dell'applicazione web, dove avvengono la  logica aziendale e l'elaborazione dei dati.

### Caratteristiche principali dell'elaborazione lato server

- **Elaborazione dei dati:** L'elaborazione lato server è ideale per le attività che comportano la gestione di dati sensibili, calcoli complessi e interazioni con database o servizi esterni.
- **Sicurezza**: Poiché il codice lato server viene eseguito su un server affidabile, è più sicuro del codice lato client, che può essere manipolato dagli utenti o intercettato dagli aggressori
- **Linguaggi lato server**: Linguaggi di programmazione come PHP, Python, Java, Ruby e altri sono comunemente utilizzati per l'elaborazione lato server.
- **Archiviazione dei dati**: L'elaborazione lato server consente di archiviare e gestire in modo sicuro i dati sensibili nei database o in altri sistemi di archiviazione

### Comunicazione e flusso di dati

- Le applicazioni Web comunicano su Internet utilizzando il protocollo HTTP
- Quando un utente interagisce con l'applicazione web facendo clic sui collegamenti o inviando moduli, il client invia richieste HTTP al server
- Il server elabora queste richieste, interagisce con il database se necessario esegue le azioni richieste e genera una risposta HTTP.
- La risposta viene quindi rinviata al client, che esegue il rendering del contenuto e lo presenta all'utente
