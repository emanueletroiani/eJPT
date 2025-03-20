Il sistema operativo **Windows memorizza** localmente le **password** degli account **utente** con hash **nel database** **SAM** (Security Accounts Manager).

**L'hashing** è il **processo** di **conversione** di un **dato in un altro valore** tramite un **algoritmo** di hashing. Il risultato è noto come hash o valore di hash.

Le versioni di Windows fino a Windows Server 2003 utilizzano due diversi tipi di hash:

- LM
- NTLM

Windows disattiva l'hashing LM e utilizza l'hashing **NTLM a partire da Windows Vista**

### Database SAM

●SAM (Security Account Manager) è un **file** di **database** responsabile della gestione degli
**account** utente e delle **password** in Windows. Tutte le password degli account utente
memorizzate nel database SAM sono sottoposte a hash.
● Il file del database **SAM** **non** **può essere copiato mentre il sistema operativo è in funzione.**
● Il kernel di Windows NT tiene bloccato il file di database SAM e di conseguenza gli
**aggressori** utilizzano solitamente **tecniche** e **strumenti in-memory (buffer overflow) per scaricare gli hash SAM dal processo LSASS.**
● Nelle versioni moderne di Windows, il database **SAM** è **crittografato** con una **syskey**.

### LM (LanMan)

- LM è l'algoritmo di hashing predefinito che è stato implementato nei sistemi operativi
Windows precedenti a NT4.0.
- Il protocollo viene utilizzato per l'hashing delle password degli utenti e il processo di
hashing può essere suddiviso nelle seguenti fasi:
    - La password è suddivisa in due parti di sette caratteri.
    - Tutti i caratteri vengono quindi convertiti in maiuscolo.
    - Ciascuna porzione viene quindi sottoposta a hashing separatamente con l'algoritmo DES.
- L'hashing LM è generalmente considerato un protocollo debole e può essere facilmente violato, soprattutto perché l'hash della password non include i sali, rendendo così efficaci gli attacchi brute-force e rainbow table contro gli hash LM.

![image](https://github.com/user-attachments/assets/c8147d26-7bf3-4c5d-ba01-b4a2ed005959)


### NTLM (NTHash)

- NTLM è un insieme di protocolli di autenticazione utilizzati in Windows per facilitare l'autenticazione tra computer. Il processo di autenticazione prevede l'utilizzo di un nome utente e di una password validi per autenticarsi con successo.
- A partire da Windows Vista, Windows disabilita l'hashing LM e utilizza l'hashing NTLM.
- Quando viene creato un account utente, questo viene **crittografato** con **l'algoritmo** di hashing **MD4**, mentre la password originale viene eliminata.
- NTLM migliora LM nei seguenti modi:
    - Non divide l'hash in due parti.
    - Maiuscole minuscole.
    - Consente l'uso di simboli e caratteri unicode

![image](https://github.com/user-attachments/assets/7564de2b-02ce-4436-a717-83ce9f2eb20e)
