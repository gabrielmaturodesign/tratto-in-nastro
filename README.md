# Tratto in Nastro

Generatore di nastri di cerchi in stile Spline, a partire da un tratto disegnato a mano
libera. Gradiente a stop liberi interpolato in OKLab, punto luce con sfumature a gusci,
export SVG / PNG / JSON.

Sito statico di un solo file: `index.html`. Nessuna build, nessuna dipendenza da
installare. L'unica risorsa esterna sono i font IBM Plex da Google Fonts; se non
rispondono, la pagina ricade sul font di sistema e continua a funzionare.

## Struttura

```
index.html    ← tutto lo strumento: markup, stile e codice
README.md     ← questo file
```

`index.html` deve restare nella cartella principale del repository: Vercel lo riconosce
come homepage senza nessuna configurazione.

## Deploy

Il progetto Vercel è collegato a questo repository. Ogni commit sul branch `main` genera
un deploy in produzione; i commit su qualsiasi altro branch generano un'anteprima con un
suo URL, utile per far vedere una variante prima di pubblicarla.

Per collegare il repository a un progetto Vercel già esistente: progetto → **Settings** →
**Git** → collega il repository. Per crearne uno nuovo: [vercel.com/new](https://vercel.com/new),
importa il repository, nessun framework da selezionare.

## Aggiornare lo strumento

**Dal browser, senza installare niente**

- Modifica al volo: apri `index.html` su GitHub, icona della matita, modifica, *Commit changes*.
- Versione nuova completa: *Add file* → *Upload files*, trascina il nuovo `index.html`
  (stesso nome), *Commit changes*. Il file viene sostituito e la cronologia resta.

In entrambi i casi Vercel ricostruisce il sito da solo nel giro di pochi secondi.

**Se qualcosa va storto**

Su Vercel, *Deployments* → scegli il deploy precedente → *Instant Rollback*. Il sito torna
alla versione di prima senza toccare il repository.

## Note per chi lo usa

- I **preset** delle impostazioni stanno nel `localStorage` del browser di chi apre lo
  strumento: restano sul suo dispositivo, non sono condivisi tra utenti, non raggiungono
  nessun server. Chi cancella i dati del sito li perde.
- Gli **export** sono generati nel browser e scaricati direttamente. Dopo il primo
  caricamento lo strumento funziona anche offline.
- Nessun cookie, nessun tracciamento, nessuna chiamata a servizi terzi oltre ai font.

## Incorporarlo in un'altra pagina

```html
<iframe
  src="https://IL-TUO-DOMINIO/"
  style="width:100%;height:820px;border:0;border-radius:12px"
  title="Tratto in Nastro"
  loading="lazy"></iframe>
```

Sotto gli 820px di altezza il pannello dei comandi diventa scomodo. Su schermi stretti lo
strumento passa da solo a layout verticale — tavola sopra, comandi sotto.

## Formato del JSON esportato

Un array di cerchi nell'ordine in cui vengono disegnati:

```json
[[cx, cy, raggio, "#rrggbb"], ...]
```
