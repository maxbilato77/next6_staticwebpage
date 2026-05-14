<<<<<<< HEAD
# next6 static webpage
Pagina statica per www.next6.it
Il repository git è collegato al servizio web static app di Azure
=======
# next6 — Static Webpage

Pagina statica per [www.next6.it](https://www.next6.it) — landing page istituzionale di next6, un'azienda IT.

## Struttura

- [index.html](index.html) — unico file HTML, tutto self-contained (CSS inline, no dipendenze locali)

## Stack

- HTML5 / CSS3 puro, zero framework
- Font: [Inter](https://fonts.google.com/specimen/Inter) via Google Fonts
- Deploy: Azure Static Web Apps (GitHub Actions)

## Effetti visivi

- Sfondo animato con griglia di punti
- Tre blob aurora con blur e movimento sinusoidale
- Logo "next6" con gradiente cyan → blu → viola e glow pulsante
- 12 particelle flottanti
- Tagline: *An IT Company*

## Deploy

Il sito viene pubblicato automaticamente su Azure Static Web Apps a ogni push su `main` tramite il workflow `.github/workflows/`.
>>>>>>> df5bf57 (Claude: ottimizzazzione del codice e miglioramento della struttura del progetto)
