# Ufficio vs. lavoro da remoto — simulatore dei costi

Un piccolo strumento interattivo per stimare la differenza reale tra il costo del tragitto verso l'ufficio e quello del lavoro da casa, mese per mese, sulla base di parametri modificabili (prezzo del carburante, distanza del tragitto, consumo dell'auto, pedaggi, costo dei pasti, elettricità e costi stagionali di riscaldamento/raffrescamento).

**[Apri il simulatore online →](#)** *https://eagleb.github.io/SmartWorkingSaving/*

## Perché

Molti confronti tra lavoro in ufficio e lavoro da casa si basano su stime approssimative. Questo strumento suddivide la decisione nelle sue componenti di costo effettive — tragitto, pasti e costo incrementale dell'elettricità/riscaldamento necessario per restare a casa durante il giorno — così puoi vedere i risultati nel tuo caso specifico e la sensibilità del risultato al prezzo del carburante o alla distanza del tragitto.

## Cosa fa

- 12 parametri regolabili tramite slider: prezzo del carburante, distanza del tragitto, consumo dell'auto, costo dei pedaggi, giorni di lavoro da remoto al mese, costo della mensa aziendale, costo del pasto a casa, consumo di PC e monitor, ore di accensione, prezzo dell'elettricità e costo aggiuntivo stagionale di riscaldamento/raffrescamento.
- Grafico a barre aggiornato in tempo reale che mostra la differenza mensile (positiva = il lavoro da remoto fa risparmiare, negativa = l'ufficio è più conveniente).
- Tabella mensile dettagliata con la suddivisione dei costi sottostanti.
- Una sezione di trasparenza in fondo alla pagina elenca tutte le formule e le ipotesi utilizzate, così il modello non è una scatola nera.

## Come funziona

La logica principale confronta i costi di una singola giornata:

```
differenza/giorno = (costo carburante del tragitto + costo mensa − costo pasto a casa) − costo aggiuntivo dell'elettricità domestica
```

Il costo aggiuntivo dell'elettricità domestica comprende il consumo giornaliero di PC e monitor più una componente stagionale (riscaldamento completo in inverno, parziale nei mesi intermedi, costo del ventilatore in estate, zero nei mesi miti). Si considera soltanto l'elettricità incrementale utilizzata restando a casa durante il giorno, non l'intera bolletta, che viene pagata indipendentemente dal luogo in cui si lavora.

I totali mensili e annuali sono ottenuti moltiplicando la differenza giornaliera per il numero di giornate di lavoro da remoto impostato.

Le formule e le ipotesi complete sono documentate direttamente nella pagina, nella sezione "Formule e assunzioni".

## Ipotesi e limitazioni

- I costi della mensa e del pasto a casa si riferiscono a un singolo pasto, non all'intera giornata.
- Si presume che elettricità, riscaldamento e raffrescamento dell'ufficio siano completamente a carico del datore di lavoro, quindi con costo zero per il dipendente.
- Non sono inclusi: usura e manutenzione dell'auto, assicurazione, tassa automobilistica, valore del tempo impiegato per il tragitto o costi indiretti del lavoro da casa (ad esempio l'allestimento dell'ufficio domestico).
- I valori predefiniti riflettono un caso reale specifico (tragitto breve, mensa agevolata, riscaldamento moderato a 16 °C): modifica gli slider per adattarli alla tua situazione.

## Tecnologia

Un unico file `index.html` autonomo. React e Babel vengono caricati da CDN (unpkg): non è necessario alcun processo di build né installare dipendenze. Funziona come pagina statica su GitHub Pages o su qualsiasi altro hosting statico.

## Esecuzione in locale

Apri semplicemente `index.html` in un browser oppure servi la cartella con un qualsiasi server di file statici:

```bash
python3 -m http.server
```

## Licenza

Licenza MIT
