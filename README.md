# Dispensa

App web in italiano per organizzare spesa alimentare, detersivi e altri acquisti con comandi vocali, inserimento manuale e suggerimenti selezionabili.

## Uso

Premi **Parla alla lista** e autorizza il microfono. Su iPhone apri direttamente in Safari. Se il servizio vocale del browser non funziona, usa **Detta dalla tastiera**.

Esempi:

- «Pane latte shampoo pantaloni»: separa i prodotti conosciuti e li distribuisce nelle tre liste.
- «Ho comprato latte e pane»: segna gli articoli acquistati.
- «Cancella il latte»: rimuove un articolo.
- «Cancella la spesa», «Cancella la lista dei detersivi», «Cancella altri».
- «Cancella tutte le liste»: svuota tutte e tre le liste.
- «Annulla»: recupera l’ultima cancellazione.
- «Stop»: interrompe il microfono.

Il riconoscimento dipende dal browser e dai servizi del dispositivo. Lo smistamento usa un dizionario locale e non riconosce ogni possibile prodotto. Gli articoli sconosciuti vanno in Altri acquisti; la lista si può correggere dal menu del prodotto.

Le liste restano nel localStorage del browser: non vengono inviate al server né sincronizzate tra familiari. Date e promemoria sono visibili nell’app, senza notifiche a pagina chiusa. Il browser può inviare l’audio al suo servizio di riconoscimento vocale. I font vengono caricati da Google Fonts.

## Sviluppo

Non servono dipendenze per l’app statica. Servire `dist/` con un server HTTP locale, per esempio `python3 -m http.server 8080 --directory dist`. Il microfono richiede HTTPS oppure localhost e un browser compatibile.

## Cloudflare Workers

Il Worker serve solamente i tre file dell’app; non registra le liste né l’audio.

```sh
node scripts/build.mjs
npx wrangler login
npx wrangler deploy
```

`wrangler.jsonc` configura il nome del Worker, il build e l’osservabilità. Le credenziali rimangono fuori dal repository.

Il cambio di dominio crea uno spazio di archiviazione distinto: le liste del vecchio indirizzo non vengono trasferite automaticamente.

## Crediti e contatti

Creata da Lukiapp. © 2026 Luca Sartori. Tutti i diritti riservati. È vietata la riproduzione, anche parziale, senza autorizzazione scritta dell’autore. Repository pubblico per consultazione; non è concessa una licenza open source.

Contatto: lukiapp.info@gmail.com. Il pulsante WhatsApp prepara un messaggio con il solo link pubblico dell’app.
