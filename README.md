Il sistema operativo Windows memorizza e cataloga tutte le azioni/eventi eseguiti sul sistema e li
archivia nel registro eventi di Windows.

- I registri eventi sono classificati in base al tipo di eventi che memorizzano:
    - **Registri delle applicazioni**: Memorizza gli eventi di applicazioni/programmi come l'avvio, l'arresto
    anomalo, ecc.
    - **Registri di sistema:** Memorizza gli eventi di sistema come l'avvio, il riavvio, ecc.
    - **Registri di sicurezza:** Memorizza gli eventi di sicurezza come la modifica della password, i
    fallimenti dell'autenticazione, ecc.
- I registri degli eventi sono accessibili tramite il Visualizzatore eventi di Windows. (event viewer)
- I registri eventi sono la prima tappa per qualsiasi investigatore forense dopo il rilevamento di una
compromissione. È quindi molto importante cancellare le proprie tracce una volta terminata la valutazione

---

Meterpreter da la possibilità di cancellare i log

- `clearev` cancella i log in event viewer
