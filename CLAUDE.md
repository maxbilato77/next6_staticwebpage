# CLAUDE.md

Questo file fornisce indicazioni a Claude Code (claude.ai/code) quando lavora con il codice in questo repository.

## Panoramica del progetto

Landing page statica per **next6 — An IT Company**, distribuita su [www.next6.it](https://www.next6.it) tramite Azure Static Web Apps. Non esiste alcun passaggio di build, script esterni o gestore di pacchetti — l'intero sito è un singolo `index.html` autocontenuto con tutto il CSS inline e un unico piccolo script inline per l'anno corrente.

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

Tutto risiede in `index.html`: una pagina bianca con il solo logo next6 centrato.

| Elemento | Selettore | Scopo |
|---|---|---|
| Sfondo | `body` | Bianco (`#ffffff`), centrato con flexbox (`align-items`/`justify-content: center`, `min-height: 100vh`) — il logo resta centrato anche ridimensionando la finestra |
| Logo | `.logo` | `<img>` che punta a `assets/images/next6-social-1200.png`, dimensionato con `clamp()` |
| Anno corrente | `.year` | `<span>` in basso a destra (`position: fixed`), popolato da un piccolo script inline con `new Date().getFullYear()` |

## Sistema di design

- **Sfondo**: `#ffffff`
- **Logo**: variante colore del marchio (nero + accento verde sul "6"), da `assets/images/` — vedi `assets/Next6 Brand Guidelines.dc.html` per varianti (colore, nero, bianco, ondark), icone e regole d'uso (spazio di rispetto, proporzioni, dimensioni minime)
- **Font UI** (solo per l'anno): stack di sistema (`-apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif`)
- **Dimensioni responsive**: il logo usa `clamp(20rem, 60vw, 56rem)`, l'anno usa `clamp(0.7rem, 1.4vw, 1rem)` — entrambi scalano con la larghezza della finestra
- **Anno**: colore grigio chiaro (`#c4c4c4`) per restare visibile ma discreto

## Asset di brand

Gli asset attuali (icone, logo in tutte le varianti, immagine social) sono in `assets/images/`. Le versioni precedenti (favicon e logo dark/light superati) sono archiviate in `assets/OLD/` e non vanno usate per nuove modifiche.

## File legacy

`index_old.html` contiene la versione precedente della pagina (tema scuro con aurora animata, griglia e particelle, descritta nel `README.md` ancora presente in repo). È tenuto solo come riferimento storico — non è servito in produzione e non va aggiornato insieme a `index.html`.
