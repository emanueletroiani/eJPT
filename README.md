### Terminologia essenziale

- **Interfaccia** - Metodi di interazione con il Metasploit Framework.
- **Modulo** - Pezzi di codice che eseguono un compito particolare; un esempio di modulo è un
exploit.
- **Vulnerabilità** - Debolezza o difetto di un sistema informatico o di una rete che può essere sfruttato.
- **Exploit** - Pezzo di codice/modulo utilizzato per sfruttare una vulnerabilità all'interno di un
sistema, servizio o applicazione.
- **Payload** - Pezzo di codice inviato al sistema di destinazione da un exploit con l'obiettivo di eseguire
comandi arbitrari o fornire accesso remoto a un aggressore.

- **Listener** - Un'utilità che ascolta una connessione in arrivo da una destinazione.

![image](https://github.com/user-attachments/assets/7f3dab2d-dc24-4695-8d1b-4b3769f43eb3)


- **Le librerie:** MSF facilitano **l'esecuzione** dei **moduli senza** dover **scrivere** il **codice** necessario per eseguirli.
    - **Un modulo:** nel contesto di MSF, è un pezzo di **codice** che può essere **utilizzato da MSF**.
        - **Exploit** - Un modulo utilizzato per **sfruttare** una **vulnerabilità**
        - **Payload** - **Codice** fornito da MSF ed **eseguito** in **remoto sul bersaglio** dopo l'exploit
        riuscito. Un esempio di payload è una **reverse shell** che avvia una connessione
        dal sistema di destinazione all'attaccante.
        - **Encoder** - Utilizzato per **codificare** i **payload** al fine di **evitare** il **rilevamento anti malware**.
        Ad esempio, shikata_ga_nai è utilizzato per codificare i payload di Windows.
        - **NOPS** - Utilizzato per **garantire** che le **dimensioni** dei **payload** siano **coerenti** e per assicurare la **stabilità** di un payload quando viene eseguito.
        - **Ausiliario** - Un modulo utilizzato per eseguire **funzionalità** aggiuntive **come** la
        **scansione** e **l'enumerazione delle porte.**

### Tipo di Payload

- **Non-staged Payload** - Payload che viene **inviato** al **sistema** di **destinazione così**
**com'è** insieme all'exploit.
- **Staged Payload** -Payload viene **inviato** al **bersaglio** in **due part**i, per cui:
La **prima parte** (stager) contiene un payload che viene utilizzato per **stabilire**
una **connessione** **inversa all'attaccante**, scaricare la seconda parte del
payload (stage) ed eseguirla.

### Stager & Stage

- **Stager** -  tipicamente utilizzati per stabilire un canale di comunicazione stabile tra l'attaccante e l'obiettivo, il payload di uno stage viene scaricato ed eseguito sul sistema di destinazione. (**meterpreter**)
- **Stage** - Componenti del payload che vengono scaricati dallo stager.
