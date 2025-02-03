SMTP è un **protocollo** di **comunicazione** utilizzato per l’invio di **email**

Utilizza la **porta** TCP **25** di default, può essere configurato anche nella porta **465** e **587 se** criptata da **ssl/tls**

1. **service postgresql start**
2. **msfconsole**
3. **workspace -a NOME**
4. **setg RHOST IP_TARGET** memorizza il target ip nei moduli
5. **setg RHOSTS IP_TARGET** memorizza il target ip nei moduli
6. **search portscan**
7. **avviare la tcp scan,** trova le porte aperte ma non le versioni dei servizi che la utilizzano
8. **search type:auxiliary name:smtp** permette la ricerca del tipo di modulo e il nome da cercare
9. **auxiliary/scanner/smtp/smtp_version** ci permette di trovare la versione del servizio
10. **auxiliary/scanner/smtp/smtp_enum** enumera gli utenti
