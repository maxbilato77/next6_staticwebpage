# next6 Static Webpage

Pagina di landing statica e ad alte prestazioni per **next6 — An IT Company**.

## 📋 Descrizione

Una landing page moderna e minimalista con animazioni GPU-accelerate. Il design presenta un'aurora boreale animata, una griglia di sfondo in movimento e particelle fluttuanti per un effetto visivo accattivante.

## 🎨 Caratteristiche

- **Design moderno** — Gradiente ciano-blu-viola con effetti aurora
- **Animazioni fluide** — Aurora glow, particelle fluttuanti, grid animata
- **Ottimizzato per performance** — GPU acceleration con `will-change`, CSS containment
- **Responsive** — Adattabile a tutti i dispositivi con `clamp()` e unità viewport
- **SEO-ready** — Meta tags, tema colore, descrizione

## 🚀 Performance

### Ottimizzazioni applicate:
- **Preconnect DNS** — Google Fonts precollegate
- **Font subsetting** — Solo pesi utilizzati (300, 400, 900)
- **GPU acceleration** — `will-change: transform, opacity` su elementi animati
- **CSS containment** — `contain: layout style paint` per isolamento visuale
- **Eliminazione code morte** — Rimosso CSS di elementi non utilizzati

**Risultato**: Animazioni fluide a 60 FPS, tempo di caricamento ottimizzato.

## 📁 Struttura

```
next6_staticwebpage/
├── index.html          # Landing page principale
├── README.md           # Questo file
└── (altri asset se presenti)
```

## 🔧 Tecnologie

- HTML5
- CSS3 (Flexbox, Grid, Gradients, Animations)
- Google Fonts (Inter)
- Azure Static Web Apps (deployment)

## 📤 Deployment

Il repository è collegato al servizio **Azure Static Web Apps** per il deploy automatico.
Ogni push a `main` attiva il deployment su [www.next6.it](https://www.next6.it)

## 📝 Note

- Nessuna dipendenza JavaScript — tutto CSS
- Compatibilità: Browser moderni (Chrome, Firefox, Safari, Edge)
- Dimensione HTML: ~12 KB (tutto inline)
