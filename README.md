**Dall'Audit al Penetration Test**

Utilizzeremo un esempio pratico per spiegare e dimostrare come funzionano gli audit di sicurezza, come vengono eseguiti e come si relazionano a un penetration test.

L'obiettivo di questa sezione è fornirti una conoscenza tacita di come i risultati degli audit di sicurezza influenzano gli obiettivi e l'ambito di un penetration test, oltre a delineare le modifiche/adattamenti necessari quando si esegue un penetration test per un'organizzazione che deve conformarsi a standard o regolamenti specifici.

### ESEMPIO

**Contesto:**

**Azienda**: **SecureTech Solutions**

**Descrizione**:

SecureTech Solutions è una società di consulenza informatica fittizia specializzata nella protezione dell'infrastruttura IT per vari clienti.

In questo esempio, dimostreremo il processo di sviluppo di una politica di sicurezza per server Linux, eseguiremo una valutazione del rischio utilizzando il framework **NIST SP 800-53**, condurremo un audit di sicurezza e testeremo le azioni di rimedio.

Questo esempio ti guiderà attraverso l'intero processo, dalla creazione iniziale della politica all'auditing e al penetration testing, evidenziando l'importanza della conformità agli standard di settore

**Obiettivi**:

- Stabilire una politica di sicurezza di base per i server Linux che sia allineata alle linee guida **NIST SP 800-53**, garantendo che i server siano configurati e gestiti in modo sicuro.
- Questa politica dovrebbe garantire che i server Linux siano protetti da accessi non autorizzati, vulnerabilità e altre minacce alla sicurezza.
- Sarà utilizzata per stabilire i requisiti di sicurezza di base per la configurazione, la manutenzione e il monitoraggio dei server Linux all'interno dell'organizzazione, in conformità con **NIST SP 800-53**.

**Processo di Sviluppo della Politica di Sicurezza: Raccolta dei Requisiti**

**Scopo**: Definire lo scopo e l'ambito della politica di sicurezza.

**Controllo degli Accessi**: Definire la gestione degli account utente, i metodi di autenticazione e la gestione dei privilegi.

**Audit e Responsabilità**: Specificare i requisiti di registrazione e le procedure di revisione dei log.

**Gestione delle Configurazioni**: Definire le configurazioni di base, le pratiche di aggiornamento del software e la gestione delle modifiche.

**Identificazione e Autenticazione**: Applicare politiche di password robuste e identificazione unica degli utenti.

**Integrità del Sistema e delle Informazioni**: Implementare protezione contro malware, monitoraggio della sicurezza e gestione delle vulnerabilità.

**Manutenzione**: Definire la manutenzione controllata e gli strumenti di manutenzione approvati.

**Politica di Sicurezza Semplice per Server Linux Allineata a NIST SP 800-53**

| **Area della Politica** | **ID Controllo** | **Dichiarazione della Politica** |
| --- | --- | --- |
| **Controllo degli Accessi (AC)** | AC-2, AC-5 | **Account Utente**: Solo il personale autorizzato avrà accesso ai server Linux. Ogni utente deve avere un account utente unico; gli account condivisi sono vietati. Gli account inattivi devono essere disabilitati o rimossi entro 30 giorni. |
| **Identificazione e Autenticazione (IA)** | IA-2, IA-5 | **Autenticazione**: Applicare politiche di password robuste: lunghezza minima di 12 caratteri, inclusi lettere maiuscole/minuscole, numeri e caratteri speciali. Utilizzare l'autenticazione basata su chiavi SSH dove possibile; disabilitare l'accesso SSH basato su password. Implementare l'autenticazione a due fattori (2FA) per gli account privilegiati. |
| **Audit e Responsabilità (AU)** | AU-2, AU-3 | **Registrazione del Sistema**: Abilitare e configurare la registrazione del sistema per catturare eventi critici. Utilizzare **rsyslog** o **journald** per la registrazione centralizzata. |
| **Audit e Responsabilità (AU)** | AU-6, AU-7 | **Revisione dei Log**: Rivedere regolarmente i log per attività sospette. Conservare i log per almeno 90 giorni. |

**Politica di Sicurezza Semplice per Server Linux Allineata a NIST SP 800-53**

| **Area della Politica** | **ID Controllo** | **Dichiarazione della Politica** |
| --- | --- | --- |
| **Gestione delle Configurazioni (CM)** | CM-2 | **Configurazione di Base**: Mantenere una configurazione di base sicura per tutti i server Linux. Utilizzare strumenti di gestione delle configurazioni (es. Ansible, Puppet) per applicare le configurazioni. |
| **Gestione delle Configurazioni (CM)** | CM-3, CM-5 | **Aggiornamenti del Software**: Mantenere il sistema e il software installato aggiornati. Applicare le patch di sicurezza entro 30 giorni dal rilascio. |
| **Identificazione e Autenticazione (IA)** | IA-5 | **Gestione delle Password**: Applicare politiche di complessità e scadenza delle password. Utilizzare gestori di password per memorizzare e gestire in modo sicuro le password. |
| **Identificazione e Autenticazione (IA)** | IA-4 | **Identificazione degli Utenti**: Garantire che tutti gli utenti siano identificati in modo univoco. |

**Politica di Sicurezza Semplice per Server Linux Allineata a NIST SP 800-53**

| **Area della Politica** | **ID Controllo** | **Dichiarazione della Politica** |
| --- | --- | --- |
| **Integrità del Sistema e delle Informazioni (SI)** | SI-3 | **Protezione da Malware**: Implementare misure di rilevamento e prevenzione del malware. Eseguire regolarmente scansioni dei server per rilevare malware. |
| **Integrità del Sistema e delle Informazioni (SI)** | SI-4 | **Monitoraggio della Sicurezza**: Monitorare i sistemi per violazioni della sicurezza o anomalie. Utilizzare strumenti come **Lynis** per eseguire audit di sicurezza regolari. |
| **Manutenzione (MA)** | MA-2 | **Manutenzione Controllata**: Eseguire manutenzione regolare sui server secondo procedure documentate. |
| **Manutenzione (MA)** | MA-3 | **Strumenti di Manutenzione**: Utilizzare solo strumenti di manutenzione approvati e garantire che siano sicu |
