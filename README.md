Il banner grabbing è una tecnica di **raccolta di informazioni** utilizzata dai penetration tester per **enumerare** le informazioni relative al **sistema operativo** di destinazione e ai **servizi** in **esecuzione** sulle **sue porte aperte.**

Per ottenere il banner possiamo utilizzare:

- Script con **nmap**
- Connessione alla porta aperta con **Netcat**.
- **Autenticazione** con il servizio (se il servizio supporta l'autenticazione), ad
esempio **SSH, FTP, Telnet** ecc.

---

- **nmap -sV --script=banner IP_TARGET**
- **nc IP_TARGET**
