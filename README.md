# 🍩 Menu QR — Fritti Artigianali

Sito statico per menu digitale con QR code. Ottimizzato per mobile.

## Struttura del progetto

```
menu-qr/
│
├── index.html              ← Pagina menu (lista prodotti)
│
├── product/
│   └── index.html          ← Pagina singolo prodotto (caricata via ?id=xxx)
│
├── data/
│   └── products.json       ← UNICA fonte dati: prodotti, ingredienti, allergeni
│
└── images/                 ← Foto dei prodotti (opzionale)
    ├── graffa-vuota.jpg
    ├── graffa-crema.jpg
    ├── graffa-marmellata.jpg
    ├── calzone-pomodoro.jpg
    ├── calzone-ricotta-salame.jpg
    └── calzone-prosciutto.jpg
```

---

## Come aggiungere o modificare prodotti

Tutto si gestisce da **`data/products.json`**. Il file ha tre sezioni:

### 1. `allergens` — mappa degli allergeni
Definisce icona, colore e label di ogni allergene. Non toccare se non aggiungi nuovi allergeni.

### 2. `ingredients` — dizionario ingredienti
Ogni ingrediente ha un `id` (usato nei prodotti) e la lista degli allergeni che contiene.

```json
"farina_00": {
  "label": "Farina 00",
  "allergens": ["glutine"]
}
```

### 3. `products` — lista prodotti
Ogni prodotto ha:

| Campo | Descrizione |
|---|---|
| `id` | Identificativo unico (usato nell'URL del QR) |
| `name` | Nome del prodotto |
| `subtitle` | Sottotitolo descrittivo |
| `category` | `"graffe"` o `"calzoni"` |
| `description` | Testo descrittivo lungo |
| `image` | Percorso immagine (es. `images/graffa-vuota.jpg`) |
| `image_placeholder_color` | Colore di sfondo se l'immagine manca |
| `ingredients` | Lista di ID ingredienti |
| `variants` | (opzionale) Varianti del prodotto |
| `tags` | `"vegetariano"`, `"bestseller"`, `"senza-latte"` |

---

## Come generare i QR code

Ogni QR deve puntare a:
```
https://TUO-UTENTE.github.io/NOME-REPO/product/?id=ID-PRODOTTO
```

Esempi:
```
https://tuosito.github.io/menu/product/?id=graffa-vuota
https://tuosito.github.io/menu/product/?id=graffa-crema
https://tuosito.github.io/menu/product/?id=calzone-ricotta-salame
```

Strumenti gratuiti per generare QR:
- [qr-code-generator.com](https://www.qr-code-generator.com/)
- [goqr.me](https://goqr.me/)

---

## Deploy su GitHub Pages (gratis)

1. Crea un repository su GitHub (es. `menu`)
2. Carica tutti i file del progetto
3. Vai su **Settings → Pages**
4. Sotto *Source* scegli `main` branch, cartella `/ (root)`
5. Clicca **Save**

Il sito sarà live su: `https://TUO-UTENTE.github.io/menu/`

> ⚠️ Se il repository è privato, GitHub Pages richiede un piano a pagamento.
> Con repository **pubblico** è completamente gratuito.

---

## Aggiornare i prodotti

Basta modificare `data/products.json` e fare commit. GitHub Pages si aggiorna automaticamente entro pochi secondi.

---

## Aggiungere le foto

Metti i file `.jpg` nella cartella `images/` con il nome indicato nel campo `image` del JSON.
Se un'immagine manca, verrà mostrato un placeholder colorato con l'emoji del prodotto.
