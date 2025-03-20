- L'MSF ci mette a disposizione diversi moduli di post exploitation sia per Windows
per Linux.
che
    - Possiamo utilizzare questi moduli di post-esercizio per enumerare le informazioni sul
    sistema Linux cui abbiamo accesso:
    - Enumerare la configurazione del sistema
    - Enumerare le variabili d'ambiente
    - Enumerare la configurazione di rete
    - Controllo VM
    - Enumerare la cronologia degli utenti

---

- `cat /etc/*issue` per sapere la distribuzione
- `uname -r` versione kernel
- `uname -a` **info varie**
- `ip a s`
- `ps aux` lista i processi
- `env`  **info varie**

exploitato il target mettere la sessione in backgroundù

- `background`
- `use post/linux/gather/enum_configs` raccoglie i file di **configurazione** presenti nelle applicazioni e nei **servizi** comunemente installati applicazioni e servizi comunemente installati, come **Apache**, **MySQL, Samba, Sendmail** etc
- `use post/multi/gather/env` stampa variabili d'ambiente del sistema operativo
- `use post/linux/gather/enum_network` raccoglie **informazioni di rete** dal sistema di destinazione
regole **IPTables**, interfacce, **informazioni wireless**, **porte aperte** e in **ascolto**, connessioni di rete attive, informazioni **DNS e SSH.**
- `use post/linux/gather/enum_protections` controlla se i più diffusi **meccanismi** di **protezione** del sistema sono **abilitati**, come **SMEP, SMAP, SELinux, PaX e grsecurity**.
    - **notes** apre le note salvate
- `use post/linux/gather/enum_system` raccoglie informazioni sul sistema come pacchetti installati, servizi installati, **informazioni sul hard disks**, **elenco degli utenti**, cronologia di bash degli utenti e **cron jobs**
- `use post/linux/gather/checkcontainer` rileva se il target utilizza un **container (**tipo VM ma migliore) ****come **Docker**, **WSL**, **LXC**, **Podman** e **systemd nspawn**.
- `use post/linux/gather/checkvm` rileva se il target utilizza una **VM**  come: **Hyper-V, VMWare, VirtualBox, Xen, and QEMU/KVM.**
- `use post/linux/gather/enum_users_history` ottiene queste specifiche info: **shell history, MySQL history, PostgreSQL history, MongoDB history, Vim history, lastlog, and sudoers**. SE L’UTENTE HA DIGITATO PASSWORD POSSIAMO VEDERLE
