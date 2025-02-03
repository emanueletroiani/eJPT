Per operare con successo come penetration tester, è fondamentale comprendere quando, come e perché vengono eseguiti gli audit di sicurezza e come si relazionano e influenzano il penetration testing.

La ragione di questa importanza è che gli audit di sicurezza e il penetration testing sono due tipi separati di valutazioni di sicurezza che hanno i propri obiettivi, ambiti e risultati desiderati.

Inoltre, data la separazione, è importante capire quando ciascuno viene eseguito (in sequenza) e se possono essere combinati in un unico processo/valutazione.

Prima di approfondire il "quando" e il "come", dobbiamo prima comprendere le differenze tra un **Audit di Sicurezza** e un **Penetration Test**, in particolare le differenze nei loro obiettivi, ambiti e risultati.

Comprendere le differenze tra i due fornirà un quadro più chiaro su quando ciascuna valutazione viene eseguita e come (potenzialmente) si integrano l'una con l'altra.

| **Aspecto** | **Audit di Sicurezza** | **Penetration Test** |
| --- | --- | --- |
| **Scopo** | Valutare la postura di sicurezza complessiva di un'organizzazione, verificando la conformità a politiche, standard e regolamenti. Si concentra sull'efficacia dei controlli di sicurezza, dei processi e delle pratiche. | Simulare attacchi reali per identificare e sfruttare vulnerabilità in sistemi, reti o applicazioni. Si concentra sulle debolezze tecniche e su come possono essere sfruttate dagli attaccanti. |
| **Ambito** | Ampio, copre vari aspetti come politiche, procedure, controlli tecnici, sicurezza fisica e conformità ai regolamenti. | Specifico per i sistemi, le reti o le applicazioni testate. L'ambito è definito per concentrarsi su aree specifiche di interesse. |
| **Metodologia** | Tipicamente include la revisione della documentazione, interviste, valutazioni tecniche e verifica della conformità agli standard di sicurezza. | Utilizza vari strumenti e tecniche per tentare di violare i sistemi, sfruttare vulnerabilità e valutare l'efficacia delle difese di sicurezza. |
| **Risultato** | Identifica lacune nelle politiche, procedure e controlli di sicurezza. Fornisce raccomandazioni per migliorare la sicurezza complessiva e garantire la conformità. | Fornisce una valutazione dettagliata delle vulnerabilità e dei potenziali vettori di attacco. Offre raccomandazioni per mitigare i rischi identificati e migliorare le difese di sicurezza. |
| **Frequenza** | Spesso eseguito su base regolare (es. annualmente o biennalmente) o come richiesto dai regolamenti di conformità. | Tipicamente eseguito quando necessario, ad esempio dopo cambiamenti significativi ai sistemi, su base regolare o come parte dei requisiti di conformità. |

# **Approccio Sequenziale**

1. **Eseguire prima l'Audit di Sicurezza**: Le aziende spesso conducono prima un audit di sicurezza per valutare la loro postura di sicurezza complessiva, garantire la conformità ai regolamenti e identificare aree di miglioramento nelle politiche e procedure.
2. **Condurre il Penetration Test successivamente**: Sulla base dei risultati dell'audit, può essere eseguito un penetration test per valutare l'efficacia dei controlli tecnici e identificare vulnerabilità specifiche.

**Vantaggi dell'Approccio Sequenziale**

- **Fornisce una visione completa della sicurezza**: sia dal punto di vista delle politiche che da quello tecnico.
- **Identifica e affronta lacune**: sia nei controlli procedurali che in quelli tecnici.
- **Aiuta a prioritizzare gli sforzi di rimedio**: basandosi sui risultati dell'audit.

# **Approccio Combinato**

**Integrare Audit di Sicurezza e Penetration Testing**: Alcune organizzazioni scelgono di combinare audit di sicurezza e penetration test, spesso attraverso una valutazione di sicurezza olistica che incorpora entrambi gli elementi.

**Vantaggi**:

- **Semplifica il processo di valutazione**: combinando valutazioni di politiche, procedure e aspetti tecnici.
- **Fornisce un quadro più completo**: della postura di sicurezza dell'organizzazione in un unico impegno.
- **Può essere più efficiente e conveniente**: affrontando sia la conformità che le vulnerabilità tecniche contemporaneamente.

### **Esempio: Approccio Sequenziale**

- Consideriamo un'organizzazione fittizia, **"SecurePayments Inc."**, che elabora transazioni con carte di credito e deve conformarsi agli standard PCI DSS.
- In questo esempio, **SecurePayments Inc.** sta utilizzando un approccio sequenziale per valutare la propria postura di sicurezza. L'organizzazione ha già eseguito un audit di sicurezza attraverso una società di audit indipendente e sta utilizzando i risultati del rapporto di audit come base per il piano di rimedio.
- Come parte del piano di rimedio, l'organizzazione ha deciso di assumere te (o la tua azienda) per eseguire un penetration test con un focus sulla conformità PCI DSS.

### **Esempio: Approccio Sequenziale**

- L'audit esterno eseguito dalla società di audit indipendente ha evidenziato i seguenti risultati:
    - **Crittografia inadeguata** per i dati dei titolari di carte durante la trasmissione.
    - **Controlli di sicurezza di rete deboli** e monitoraggio del traffico insufficiente.
    - **Politiche di controllo degli accessi deboli** che consentono permessi eccessivi.
    - **Procedure di risposta agli incidenti obsolete**.
- Le raccomandazioni corrispondenti per i risultati sopra descritti sono:
    - Implementare **protocolli di crittografia robusti** per i dati in transito.
    - Revisionare le **politiche di controllo degli accessi** per seguire il principio del minimo privilegio.
    - Aggiornare e testare regolarmente le **procedure di risposta agli incidenti**.

**L'azienda ha seguito il ciclo di vita del processo di auditing di sicurezza descritto nel video "Processo/Ciclo di Vita dell'Auditing di Sicurezza" e ha apportato i miglioramenti necessari in base alle raccomandazioni.**

**Obiettivi:**

- Dopo aver apportato le modifiche/miglioramenti necessari in base ai risultati e alle raccomandazioni del rapporto di audit esterno, **SecurePayments Inc.** ti ha assunto per testare i controlli tecnici e le misure di sicurezza implementate in base ai risultati dell'audit, per verificare se sono efficace

### **Esempio: Approccio Sequenziale**

**Fase 1: Pianificazione e Preparazione:**

Durante la fase iniziale, identifichi che l'ambito PCI DSS include l'ambiente dei dati dei titolari di carte (CDE). Rivedi i diagrammi di rete di **SecurePayments Inc.** e i questionari di autovalutazione PCI DSS per comprendere le loro attuali misure di sicurezza e lo stato di conformità.

**Obiettivi:**

- Definire l'ambito del penetration test per concentrarsi sulle aree identificate nell'audit, come la sicurezza di rete e le vulnerabilità delle applicazioni.
- Stabilire un programma di testing e informare gli stakeholder.

**Fase 2: Raccolta delle Informazioni e Ricognizione:**

Raccogli informazioni sulle politiche di sicurezza di **SecurePayments Inc.**, come le loro politiche di controllo degli accessi, gli standard di crittografia e le procedure di risposta agli incidenti.

Rivedi anche il loro ultimo rapporto di audit PCI DSS per identificare le aree di preoccupazione evidenziate dagli auditor.

**Fase 3: Esecuzione del Penetration Test:**

- Esegui **scansioni di rete**, enumerazione e valutazioni delle vulnerabilità per identificare debolezze, configurazioni errate o vulnerabilità.
- Tenta di sfruttare le vulnerabilità identificate per valutarne l'impatto.
- Testa l'efficacia delle nuove implementazioni di crittografia e dei controlli di accesso.

**Fase 4: Risultati e Raccomandazioni:**

**Risultato:** Il penetration test ha scoperto ulteriori vulnerabilità:

- Un'interfaccia amministrativa esposta che consente accessi non autorizzati.
- Vulnerabilità di **SQL injection** in un'applicazione web rivolta ai clienti.

**Raccomandazioni:**

- Proteggere l'interfaccia amministrativa implementando ulteriori controlli di autenticazione e accesso.
- Correggere le vulnerabilità di SQL injection e condurre una revisione approfondita della sicurezza dell'applicazione.

### **Riepilogo dell'Approccio Sequenziale**

- **Risultati dell'Audit di Sicurezza**:
    - Identificazione di lacune di conformità e carenze nelle politiche.
    - Raccomandazioni per migliorare le politiche e le procedure di sicurezza.
- **Risultati del Penetration Test**:
    - Rivelazione di vulnerabilità tecniche specifiche.
    - Raccomandazioni mirate per affrontare queste debolezze tecniche
