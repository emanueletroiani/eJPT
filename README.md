SESSIONE METERPRETER

1. `background`
- `post/multi/gather/ssh_creds` restituisce i valori delle chiavi **id_rsa.pub** e **id_rsa**
- `post/multi/gather/docker_creds` colleziona il contenuto della docker directory
- `post/linux/gather/hashdump` dumb delle password degli utenti
- `post/linux/gather/ecryptfs_creds` colleziona il contenuto directory .ecrypts di tutti gli utenti sul. i file possono essere craccati con with John the Ripper
- `post/linux/gather/enum_psk` raccoglie le **credenziali Wireless** come: n**ome dell'access point** e chiave precondivisa, file di **configurazione** delle **connessioni**.
- `post/multi/gather/enum_hexchat`
- `post/linux/gather/phpmyadmin_credsteal` raccoglie le credenziali phpMyAdmin
- `post/linux/gather/pptpd_chap_secrets` **raccoglie user, server, password e IP dal target se usa una VPN**
- `post/linux/manage/sshkey_persistence`aggiungerà una chiave SSH a un utente specificato (o a tutti), per consentire a l'accesso remoto via SSH in qualsiasi momento.
1. `loot` mostra tutto cio’ che abbiamo trovato
