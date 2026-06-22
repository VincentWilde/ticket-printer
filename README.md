# ticket-printer

## Accesso protetto (cifratura lato client)

La pagina `ticket_v2.html` viene **cifrata con AES-256 (StatiCrypt)** durante il
deploy su GitHub Pages. Sul sito pubblicato finisce solo il testo cifrato: la
password **non è mai presente** nell'HTML né nel repository. Chi apre la pagina
deve inserire la password per decifrarla nel proprio browser.

### Configurazione (da fare una volta sola)

1. Vai su **Settings → Secrets and variables → Actions → New repository secret**.
2. Crea un secret con:
   - **Name:** `PAGE_PASSWORD`
   - **Secret:** la password che vuoi usare per accedere alla pagina.
3. Lancia il workflow *Deploy to GitHub Pages* (parte da solo a ogni push su
   `main`, oppure manualmente da **Actions → Run workflow**).

Per cambiare la password basta aggiornare il secret `PAGE_PASSWORD` e rilanciare
il deploy. Una volta inserita, la password resta memorizzata nel browser per 30
giorni (non va reinserita a ogni visita).

> Nota: `index.html` è un semplice redirect senza contenuti sensibili, quindi
> resta in chiaro e rimanda alla pagina cifrata.
