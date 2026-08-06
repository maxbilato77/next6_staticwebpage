# Linee guida del logo next6

Documento di riferimento per l'utilizzo corretto del marchio **next6** sul sito web, sui materiali digitali e sulle comunicazioni ufficiali. Tutti i file sono in formato **SVG vettoriale**, scalabili a qualsiasi dimensione senza perdita di qualità.

---

## 1. Set di file

Il set è composto da quattro file SVG suddivisi in due categorie.

### Logo principale (wordmark)

Scritta "next6" da utilizzare come marchio principale: header del sito, intestazioni, firme email, presentazioni, materiale stampato.

| File | Sfondo consigliato | Uso tipico |
|---|---|---|
| `next6-logo-dark.svg` | scuro (#050508 o simili) | header del sito, dark mode, materiale notturno |
| `next6-logo-light.svg` | chiaro (#ffffff o simili) | documenti, light mode, stampa |

### Favicon (monogramma)

Sigla "n6" inscritta in un badge quadrato con angoli arrotondati. Da utilizzare dove serve un'icona compatta: favicon del browser, app icon, avatar social, badge in firma.

| File | Sfondo del badge | Uso tipico |
|---|---|---|
| `next6-favicon-dark.svg` | nero (#050508) | favicon su browser chiari, avatar social |
| `next6-favicon-light.svg` | bianco (#ffffff) | favicon su browser scuri, contesti minimali |

---

## 2. Tipografia

| Caratteristica | Valore |
|---|---|
| Famiglia | **Inter** (Google Fonts) |
| Peso | **900 — Black** |
| Crenatura (letter-spacing) | **−0,04em** (≈ −6,4px su 160px di altezza testo) |
| Stile | tutto minuscolo, nessuna maiuscola |
| Fallback | `'Helvetica Neue', Arial, sans-serif` |

Il font Inter viene importato direttamente dentro ogni file SVG tramite `@import` da Google Fonts, in modo da garantire la corretta resa anche quando l'SVG viene usato come immagine isolata (`<img src>`). Se si incorpora l'SVG inline in una pagina dove Inter è già caricato, l'`@import` può essere rimosso per ottimizzare le richieste di rete.

---

## 3. Colori

### Gradiente principale

Il logo utilizza un **gradiente lineare diagonale a 135°** che attraversa tre tonalità: ciano → blu → viola. Il gradiente si estende sull'intera parola "next6" (e sul monogramma "n6"), quindi ogni lettera prende la porzione di colore che le tocca in posizione: non esistono colori "per lettera".

#### Versione su sfondo scuro

| Stop | Posizione | Colore | HEX |
|---|---|---|---|
| 1 | 0% | ciano elettrico | `#00d4ff` |
| 2 | 50% | blu cobalto | `#2d6aff` |
| 3 | 100% | viola digitale | `#6B21F7` |

Definizione CSS equivalente:

```css
background: linear-gradient(135deg, #00d4ff 0%, #2d6aff 50%, #6B21F7 100%);
```

#### Versione su sfondo chiaro

Le tre tonalità sono **leggermente desaturate e scurite** per garantire un contrasto sufficiente sul bianco.

| Stop | Posizione | Colore | HEX |
|---|---|---|---|
| 1 | 0% | ciano profondo | `#00b8e0` |
| 2 | 50% | blu cobalto | `#2d6aff` |
| 3 | 100% | viola scuro | `#5a18d6` |

### Colori di supporto

| Ruolo | HEX | Nota |
|---|---|---|
| Sfondo brand scuro | `#050508` | nero quasi puro, valore di `theme-color` del sito |
| Sfondo brand chiaro | `#ffffff` | bianco puro |
| Testo tagline (su scuro) | `rgba(255,255,255,0.35)` | grigio chiaro semi-trasparente |

---

## 4. Dimensioni e proporzioni

### Logo (wordmark)

- **viewBox SVG:** `0 0 600 200`
- **Proporzione:** 3 : 1 (larghezza : altezza)
- **Dimensione minima consigliata sul web:** **120 px di larghezza**. Sotto questa soglia la scritta perde leggibilità.
- **Dimensione tipica nell'header del sito:** 160–220 px di larghezza.
- **Dimensione di riferimento per stampa:** non scendere sotto i 25 mm di larghezza.

### Favicon (monogramma)

- **viewBox SVG:** `0 0 256 256`
- **Proporzione:** 1 : 1 (quadrato)
- **Raggio degli angoli:** 48 px (≈ 18,75% del lato) — coerente con il radius delle app icon iOS/Android moderne.
- **Dimensione minima consigliata:** **16 × 16 px** (favicon classica). A questa misura il monogramma "n6" resta leggibile, mentre il wordmark non sarebbe utilizzabile.
- **Dimensioni tipiche di esportazione PNG** per favicon multi-piattaforma: 16, 32, 48, 96, 180 (Apple touch), 192, 512 px.

### Margine di rispetto (clear space)

Intorno al logo lasciare uno spazio libero da altri elementi pari ad **almeno l'altezza della "x" della scritta** (circa 1/3 dell'altezza totale del wordmark). Per la favicon, evitare di racchiuderla in ulteriori cornici o contenitori colorati: il badge integrato è già il suo contenitore.

---

## 5. Regole d'uso

### Cosa fare
- Usare sempre la versione corretta in base allo sfondo (dark/light).
- Mantenere le proporzioni originali del file SVG.
- Preferire l'SVG al PNG ovunque sia possibile.
- Per la favicon su iOS è consigliato esportare in PNG 180×180 px partendo dal file `next6-favicon-dark.svg`.

### Cosa evitare
- Non modificare il gradiente, né sostituirlo con colori piatti senza necessità.
- Non distorcere, ruotare o inclinare il logo.
- Non aggiungere ombre, contorni, riflessi o effetti di testo.
- Non riscrivere "next6" con un altro font: il marchio è la combinazione specifica testo + Inter Black 900.
- Non usare la versione "dark" su sfondi chiari e viceversa: il contrasto risulterebbe insufficiente.
- Non separare le due componenti del monogramma (badge + "n6"): vanno sempre insieme.

---

## 6. Integrazione tecnica

### HTML — header del sito (esempio)

```html
<a href="/" class="brand">
  <img src="/assets/next6-logo-dark.svg" alt="next6" width="180" height="60">
</a>
```

### HTML — favicon

```html
<link rel="icon" type="image/svg+xml" href="/assets/next6-favicon-dark.svg">
<link rel="apple-touch-icon" href="/assets/next6-favicon-dark-180.png">
```

### SVG inline

Quando il logo è incorporato direttamente nell'HTML (preferibile per ridurre le richieste HTTP e applicare animazioni CSS), si può rimuovere l'`@import` interno e affidarsi al font Inter già caricato nella pagina.

### Generazione della favicon completa

A partire da `next6-favicon-dark.svg` si possono generare tutti i formati PNG necessari (16, 32, 48, 96, 180, 192, 512 px) e il file `.ico` multi-risoluzione tramite strumenti come [realfavicongenerator.net](https://realfavicongenerator.net).

---

## 7. Riferimenti rapidi

| Elemento | Valore |
|---|---|
| Nome del marchio | **next6** (tutto minuscolo, nessuno spazio) |
| Tagline ufficiale | *An IT Company* |
| Font del logo | Inter Black 900 |
| Crenatura | −0,04em |
| Gradiente brand (scuro) | `#00d4ff → #2d6aff → #6B21F7` a 135° |
| Gradiente brand (chiaro) | `#00b8e0 → #2d6aff → #5a18d6` a 135° |
| Sfondo brand scuro | `#050508` |
| Proporzione logo | 3 : 1 |
| Proporzione favicon | 1 : 1, radius 48/256 |
