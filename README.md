### Componenti della risposta HTTP

Response Headers

- Le intestazioni più comuni includono:
    - **Content-Type**: Il tipo di media del contenuto della risposta (ad esempio, text/html, application/json).
    - **Content-Length**: La dimensione del corpo della risposta in byte.
    - **Set-Cookie**: Utilizzato per impostare i cookie sul lato client per le richieste successive.
    - **Cache-Control**: Direttive per il comportamento della cache.

### Response Body (Optional)

Il corpo della risposta contiene il contenuto effettivo della risposta. Ad esempio, nel caso di una pagina HTML, il corpo della risposta conterrà il markup HTML.

### HTTP Request Response Example

- In risposta alla richiesta HTTP, il server web risponde con la risorsa richiesta, preceduta da un gruppo di nuove intestazioni di risposta HTTP.
- Queste nuove Response Headers del server Web verranno utilizzate dal browser Web per interpretare il contenuto della risposta.
- Il frammento di codice riportato di seguito è un esempio di risposta tipica del server Web.
- **Nota**: il corpo del contenuto della risposta/pagina è stato omesso in quanto non rilevante in questo momento.
- Analizziamo in alcune di queste Headers di risposta HTTP.

![image](https://github.com/user-attachments/assets/b541bad9-1f47-42d2-9d2d-9af191e503e6)

### HTTP Response Status-Line

La prima riga di una risposta HTTP è la riga di stato, costituita versione del protocollo (HTTP 1.1) seguita dal codice di stato HTTP (200) e relativo significato testuale (OK).

![image](https://github.com/user-attachments/assets/f4336054-1b1d-4067-94de-f2efe710337c)

### CODICI COMUNI

- **200 OK:** La richiesta è andata a buon fine e il server ha restituito i dati richiesti
- **301 Moved Permanently:** La risorsa richiesta è stata spostata in modo permanente su un nuovo URL e il client deve utilizzare il nuovo URL per tutte le richieste future.
- **302 Found:** La risorsa richiesta si trova temporaneamente in un URL diverso. Questo codice viene comunemente usato per i reindirizzamenti temporanei, ma spesso è meglio usare 303 o 307.
- **400 Bad Request**: Il server non può elaborare la richiesta a causa di un errore del client (ad esempio, sintassi della richiesta non formata).
- **401 Non autorizzato**: È richiesta l'autenticazione e il client deve fornire credenziali valide per accedere alla risorsa richiesta.
- **403 Forbidden:** Il server ha compreso la richiesta, ma il client non ha il permesso di accedere alla risorsa richiesta.
- **404 Not Found:** La risorsa richiesta non è stata trovata sul server.
- **500 Internal Server Error:** Il server ha riscontrato un errore durante l'elaborazione della richiesta e la causa specifica non è stata fornita

### HTTP Response Date Header

- L’Header "Data" in una risposta HTTP è utilizzata per indicare la data e l'ora in cui la risposta è stata generata dal server.
- Aiuta i client e gli intermediari a capire la freschezza della risposta e a sincronizzare l'ora tra il server e il client.

  ![image](https://github.com/user-attachments/assets/aed6cf3e-90c9-4518-bab2-d750fc81fb14)

  ### HTTP Response Cache-Control Header

- Le Cache headers consentono al browser e al server di concordare le regole di caching. Consentono ai server Web di indicare ai client per quanto tempo possono memorizzare nella cache la risposta e in quali condizioni devono riconvalidarla con il
server.
- Ciò contribuisce a ottimizzare le prestazioni e l'efficienza delle applicazioni web, riducendo le richieste di rete non necessarie

![image](https://github.com/user-attachments/assets/dda2dcba-7fb2-4586-9ae8-af3da7743d64)

Direttive Cache-Control

- **Public**: Indica che la risposta può essere messa in cache da eventuali cache intermedie (come i server proxy) e condivisa da diversi utenti.
- **Private**: Specifica che la risposta è destinata a un utente specifico e non deve essere memorizzata nella intermedia.
- **no-cache:** Indica al client di riconvalidare la risposta con il server prima di usare la versione in cache. Non impedisce la memorizzazione nella cache, ma richiede la riconvalida.
- **no-store:** Indica al client e alle cache intermedie di non memorizzare alcuna versione della risposta. Assicura che la risposta non venga memorizzata nella cache in nessuna forma.
- **max-age=<SECONDS>** Specifica il tempo massimo, in secondi, in cui la risposta può essere messa in cache dal client. Dopo questo periodo, il client deve riconvalidare la risposta con il server

### HTTP Response Content-Type Header

- L'Header "Content-Type" in una risposta HTTP è utilizzata per indicare il tipo di supporto del contenuto della risposta.
- Indica al client il tipo di dati che il server sta inviando, in modo che il client possa gestirli in modo appropriato.

  ![image](https://github.com/user-attachments/assets/5d066665-8225-40ef-81ec-81805bba24ca)

  ### HTTP Response Content-Encoding Header

- L’header "Content-Encoding" in una risposta HTTP viene utilizzata per specificare la codifica di compressione applicata al contenuto della risposta.
- Indica al client come il server ha codificato i dati di risposta, consentendo al client di decodificare e decomprimere correttamente i dati.

  ![image](https://github.com/user-attachments/assets/4bb1bf6c-2219-4d41-8b07-8f3cae927fca)


### HTTP Response Server Header

- L’Header Server mostra il banner del server Web, ad esempio Apache, Nginx, IIS ecc.
- Google utilizza un server web personalizzato: gws (Google Web Server).

  ![image](https://github.com/user-attachments/assets/c997b51c-3a9b-4710-baaa-8deb9c735403)



  
