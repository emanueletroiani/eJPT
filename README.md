### Componenti della richiesta HTTP

### **Request line**

- La riga di richiesta è la prima riga di una richiesta HTTP e contiene i seguenti tre componenti:
    - **Metodo HTTP** (ad esempio, GET, POST, PUT, DELETE, ecc.): Indica il tipo di richiesta effettuata.
    - **URL** (Uniform Resource Locator): L'indirizzo della risorsa a cui il client vuole accedere.
    - V**ersione HTTP**: La versione del protocollo HTTP utilizzato (ad esempio, HTTP/1.1)

---

ESEMPIO

- Esaminiamo in dettaglio una richiesta HTTP. Di seguito sono riportati i dati contenuti in una richiesta inviata quando si naviga su [www.google.com](http://www.google.com/) con un browser web.

![image](https://github.com/user-attachments/assets/88ff4b61-02d9-4772-ba17-05ef98cd812f)

---

### **Request Headers**

- Le intestazioni forniscono informazioni aggiuntive sulla richiesta. Le
intestazioni più comuni includono:
    - **User-Agent:** Informazioni sul client che effettua la richiesta (ad esempio, il tipo di browser).
    - **Host**: Il nome dell'host del server.
    - **Accept:** I tipi di media che il client può gestire nella risposta (ad esempio, HTML, JSON).
    - **Autorizathion**: Credenziali per l'autenticazione, se richieste.
    - **Cookie:** Informazioni memorizzate sul lato client e inviate al server a ogni richiesta.

---

ESEMPIO

- Viene avviata una richiesta HTTP a [www.google.com](http://www.google.com/). Quelle che si vedono qui sono le intestazioni (HTTP Request Headers) di questa richiesta.
- Si noti che la connessione a [www.google.com](http://www.google.com/) sulla porta 80 viene avviata prima di inviare i comandi HTTP al server web.

![image](https://github.com/user-attachments/assets/b8289d69-26af-4b9c-9a14-775e94a23740)

### **Request Body (opzionale)**

- Alcuni metodi HTTP (come POST o PUT) includono un corpo della richiesta in cui i dati vengono inviati al server, in genere in formato JSON o di dati di forma.

---

### Metodi di richiesta HTTP

- I metodi di richiesta HTTP (verbi HTTP) forniscono un modo standardizzato per client e server di comunicare e interagire con le risorse sul web. La scelta del metodo appropriato dipende dal tipo di operazione che deve essere eseguita sulla risorsa.
- **GET** è il metodo di richiesta predefinito utilizzato quando si effettua una richiesta a un'applicazione web, in questo caso stiamo cercando di connetterci a [www.google.com](http://www.google.com/).

![image](https://github.com/user-attachments/assets/9fec06b7-ef3d-43f4-a498-0797001b7498)

- **GET**: Il metodo GET viene utilizzato per recuperare dati dal server. Richiede la risorsa specificata nell'URL e non modifica lo stato del server. È un metodo sicuro e idempotente, il che significa che fare la stessa richiesta GET più volte non dovrebbe avere effetti collaterali.
- **POST**: Il metodo POST è utilizzato per inviare dati che devono essere elaborati dal server. In genere include dati nel corpo della richiesta e il server può eseguire azioni basate su tali dati. Le richieste POST possono causare modifiche allo stato del server e non sono idempotenti.
- **PUT**: Il metodo PUT viene utilizzato per aggiornare o creare una risorsa sul server all'URL specificato. Sostituisce l'intera risorsa con la nuova rappresentazione fornita nel corpo della richiesta. Se la risorsa non esiste, PUT può crearla.
- **DELETE**: Il metodo DELETE viene utilizzato per rimuovere dal server la risorsa specificata dall'URL. Dopo una richiesta DELETE andata a buon fine, la risorsa non sarà più disponibile su quell'URL.
- **PATCH**: Il metodo PATCH viene utilizzato per applicare modifiche parziali a una risorsa. È simile al metodo PUT, ma aggiorna solo parti specifiche risorsa anziché sostituirla interamente.
- **HEAD**: Il metodo HEAD è simile al metodo GET, ma recupera solo le intestazioni della risposta e non il corpo della risposta. Viene spesso usato per controllare le intestazioni, ad esempio per verificare l'esistenza di una risorsa o le date di modifica
- **OPTIONS**: Il metodo OPTIONS viene utilizzato per recuperare informazioni sulle opzioni di comunicazione disponibili per la risorsa di destinazione. Consente ai client determinare i metodi e le intestazioni supportate per una particolare risorsa.

---

### HTTP Request UTR/PATH

- L'indirizzo della risorsa/URI a cui il client vuole accedere.
- La pagina iniziale di un sito web è sempre "/". Naturalmente si possono richiedere altre pagine, ad esempio: /downloads/index.php.
- La richiesta si riferisce sempre alla cartella principale per specificare il file richiesto (da qui l'iniziale "/").

![image](https://github.com/user-attachments/assets/830f5e8e-2316-4995-a787-80d440b25ea7)

### HTTP Request protocol

- È la versione del protocollo HTTP con cui il browser vuole comunicare (HTTP 1.0/HTTP 1.1).

![image](https://github.com/user-attachments/assets/9acd1b92-35b9-4cb3-b720-8afc7ffb4f18)

---

### HTTP Request Host Header

- Questo è l'inizio delle intestazioni delle richieste HTTP. Le intestazioni HTTP hanno la seguente struttura: Header-name:Header-Value
- L’Header Host consente a un server web di ospitare più siti web su un singolo IP. indirizzo. Il nostro browser specifica nell'intestazione Host a quale sito web interessati.

![image](https://github.com/user-attachments/assets/39ce330a-2aca-4f6a-ae72-dd03cb36c4e6)

- Dopo ogni intestazione di richiesta, si trova il valore corrispondente. In questo vogliamo accedere all'Host [www.google.com](http://www.google.com/).
- Nota: il valore Host+ Path si combina per creare l'URL completo richiesto: la home page di [www.google.com/](http://www.google.com/)

---

### HTTP Request User-Agent

- Lo User-Agent viene utilizzato per specificare e inviare il browser, la versione del browser, il sistema operativo e la lingua al server web remoto.
- Tutti i browser web hanno una propria stringa di identificazione dell'user-agent. In questo modo la maggior parte dei siti web riconosce il tipo di browser in uso.

![image](https://github.com/user-attachments/assets/f213ab1b-058e-46e9-8f46-eb007b4f9167)

---

### HTTP Request Accept Header

- L'intestazione Accept viene utilizzata dal browser per specificare quali tipi di documenti/file devono essere restituiti dal server web come risultato di questa richiesta.

![image](https://github.com/user-attachments/assets/24ebb581-6ade-4928-a5f7-9e9536bf9bc3)

---

### HTTP Request Accept-Encoding

- L'intestazione Accept-Encoding è simile ad Accept e viene utilizzata per limitare la codifica del contenuto accettabile nella risposta.
- La codifica dei contenuti viene utilizzata principalmente per consentire di comprimere o trasformare un documento senza perdere il formato originale e senza perdere informazioni

![image](https://github.com/user-attachments/assets/c2366396-1a97-4a79-906a-64c492fd7a25)

---

### HTTP Request Connection Header

- Quando si utilizza HTTP 1.1, è possibile mantenere/riutilizzare la connessione al server web remoto per un periodo di tempo non specificato utilizzando il valore "keep-alive".
- Indica che tutte le richieste al server web continueranno a essere inviate attraverso questa connessione senza iniziare ogni volta una nuova connessione (come in HTTP 1.0).

![image](https://github.com/user-attachments/assets/fb7a01d9-ced8-4aac-bbda-b9c2a14131b5)







