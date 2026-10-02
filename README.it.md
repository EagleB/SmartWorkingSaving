# SmartWorkingSaving

Un simulatore interattivo leggero per confrontare il costo di una giornata in ufficio con quello di una giornata lavorata da casa, includendo totali mensili, risparmio annuale e impatto CO2.

Demo live: https://eagleb.github.io/SmartWorkingSaving/

## Panoramica

Questo progetto aiuta a rispondere a una domanda molto concreta: il lavoro da remoto conviene davvero rispetto al tragitto in ufficio, una volta considerati carburante, pedaggi, costo dei pasti, elettricità e costi stagionali di riscaldamento/raffrescamento domestico?

Il calcolatore è pensato per essere trasparente: mostra il delta mensile, il risparmio annuale e la CO2 evitata lavorando da remoto, oltre a esporre le formule e le assunzioni utilizzate.

## Funzionalità attuali

- Parametri regolabili per:
  - prezzo del carburante o costo ricarica EV
  - distanza casa-ufficio
  - consumo auto / consumo EV
  - pedaggi
  - giorni di lavoro da remoto a settimana
  - settimane lavorative all'anno
  - costo mensa aziendale
  - costo pasto a casa
  - potenza PC + monitor e ore di utilizzo giornaliere
  - costo dell'elettricità
  - extra stagionali di riscaldamento/raffrescamento
- Selettore veicolo ICE/EV
- Grafico dei risparmi mensili con delta positivi/negativi
- Grafico del risparmio annuale di CO2 con numero equivalente di alberi
- Tabella dettagliata dei costi mensili
- Pannello di parametri comprimibile
- Esportazione in Excel (.xlsx) con grafici incorporati
- Interfaccia bilingue: italiano e inglese
- Sezione con formule e assunzioni in fondo alla pagina

## Come funziona il modello

Il confronto giornaliero si basa su questa idea:

```text
delta/giorno = (costo del tragitto + costo mensa - costo pasto a casa) - costo extra di elettricità domestica
```

Il costo extra di elettricità domestica include:
- il consumo del PC e del monitor durante la giornata di lavoro
- un componente stagionale per il riscaldamento in inverno e il ventilatore in estate
- nessun effetto della bolletta completa, poiché si assume che i consumi dell'ufficio siano a carico del datore di lavoro

I risultati mensili e annuali sono ottenuti moltiplicando questo delta giornaliero per i giorni di smart working e le settimane lavorative configurate.

## Ipotesi e limitazioni

- I costi del pasto sono trattati come costo di un singolo pasto, non come costo dell'intera giornata.
- Si assume che illuminazione, elettricità, riscaldamento e raffrescamento dell'ufficio siano a carico del datore di lavoro.
- Il modello non include usura e manutenzione dell'auto, assicurazione, tassa automobilistica, valore del tempo dedicato al tragitto o costi indiretti dell'ufficio domestico.
- I valori predefiniti sono esempi e devono essere adattati alla propria situazione.

## Struttura del progetto

- `index.html` — interfaccia completa, stile, formule e logica dell'app
- `README.md` — panoramica in inglese
- `README.it.md` — panoramica in italiano
- `LICENSE` — licenza MIT

## Esecuzione in locale

Puoi aprire direttamente l'app nel browser:

```bash
start index.html
```

Oppure servirla localmente:

```bash
python -m http.server
```

Poi apri http://localhost:8000 nel browser.

## Stack tecnologico

Questo progetto è una single-page app statica costruita con:

- HTML + CSS
- React via CDN
- Babel per la compilazione JSX in-browser
- ExcelJS per l'esportazione del foglio di calcolo

Non è richiesto alcun processo di build né installazione di dipendenze.

## Licenza

MIT
