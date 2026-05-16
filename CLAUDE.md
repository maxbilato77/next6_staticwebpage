# CLAUDE.md

Questo file fornisce indicazioni a Claude Code (claude.ai/code) quando lavora con il codice in questo repository.

## Panoramica del progetto

Landing page statica per **next6 — An IT Company**, distribuita su [www.next6.it](https://www.next6.it) tramite Azure Static Web Apps. Non esiste alcun passaggio di build, JavaScript esterno o gestore di pacchetti — l'intero sito è un singolo `index.html` autocontenuto con tutto il CSS inline.

## Sviluppo

Per visualizzare la pagina in locale, aprire `index.html` direttamente nel browser:

```bash
xdg-open index.html        # Linux
open index.html            # macOS
```

Non è necessario alcun server — la pagina non ha dipendenze dinamiche né chiamate API.

## Distribuzione

Ogni push su `main` attiva un deploy automatico tramite il workflow GitHub Actions in `.github/workflows/azure-static-web-apps-salmon-meadow-0c3133603.yml`. Il target di deploy è Azure Static Web Apps, usando il secret `AZURE_STATIC_WEB_APPS_API_TOKEN_SALMON_MEADOW_0C3133603`. Le anteprime delle PR vengono create automaticamente e rimosse alla chiusura della PR.

## Architettura

Tutto risiede in `index.html`. I livelli visivi, dal basso verso l'alto (ordine z-index):

| Layer | Elemento | z-index | Scopo |
|---|---|---|---|
| Griglia di punti animata | `body::before` | 0 | Griglia CSS con background-image che scivola di 40px in diagonale |
| Aurora blob | `.aurora .blob` | 0 | 3 blob radiali sfocati in ciano/blu/viola |
| Vignettatura scura | `.overlay` | 1 | `radial-gradient` che sfuma verso `#050508` ai bordi |
| Particelle fluttuanti | `.particles .particle` | 2 | 12 piccoli punti che salgono con i keyframe `particleFloat` |
| Bagliore ambientale | `body::after` | 3 | Bagliore radiale centrato con pulsazione lenta |
| Contenuto principale | `.content` | 10 | Logo + tagline, centrati con flexbox |

## Sistema di design

- **Sfondo**: `#050508`
- **Gradiente brand**: `#00d4ff` → `#2d6aff` → `#6B21F7` (135°), applicato al testo del logo e agli aurora blob
- **Font**: Inter (300, 400, 900) da Google Fonts; preconnesso per le performance
- **Dimensioni responsive**: il logo usa `clamp(5rem, 12vw, 14rem)`, il tagline usa `clamp(0.85rem, 1.8vw, 1.2rem)`

## Vincoli di performance

Mantenere questi elementi quando si modificano gli elementi animati:

- `will-change: transform, opacity` su tutti gli elementi animati (aurora blob, particelle, bagliore ambientale)
- `contain: layout style paint` su `.aurora` e `.particles` per isolare i livelli di compositing
- La griglia animata usa `will-change: transform` per rimanere sulla GPU
