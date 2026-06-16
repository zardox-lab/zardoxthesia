# ZardoXthesia PWA — Deployment Guide

## Files in this package
```
index.html      ← app principale
manifest.json   ← metadati PWA (nome, icone, colori)
sw.js           ← service worker (cache offline)
icon-192.svg    ← icona app 192×192
icon-512.svg    ← icona app 512×512
```

---

## Hosting gratuito consigliato: GitHub Pages

1. Crea un account su https://github.com (gratuito)
2. Crea un nuovo repository pubblico, es. `zardoxthesia`
3. Carica tutti i file di questa cartella nel repository
4. Vai su **Settings → Pages → Source: main branch / root**
5. L'app sarà disponibile su `https://zardox-lab.github.io/zardoxthesia/`

---

## Alternative hosting gratuite

| Servizio | URL | Note |
|----------|-----|-------|
| Netlify | netlify.com | Drag & drop della cartella, HTTPS automatico |
| Vercel | vercel.com | Deploy istantaneo |
| Cloudflare Pages | pages.cloudflare.com | CDN globale |

**Tutti i servizi sopra forniscono HTTPS automatico**, requisito obbligatorio per:
- accesso alla camera (MediaPipe Hand Tracking)
- installazione come PWA

---

## Come installare su iPhone

1. Apri Safari e vai all'URL dell'app
2. Tocca il pulsante **Condividi ⬆** (in basso al centro)
3. Scorri e tocca **"Aggiungi a schermata Home"**
4. Conferma il nome → tocca **Aggiungi**

L'app apparirà come icona sulla schermata home, si aprirà a schermo intero senza barra URL, funzionerà offline dopo il primo caricamento.

---

## Limitazioni iOS Safari vs App Store nativa

| Funzione | PWA iOS | App nativa |
|----------|---------|-----------|
| Funziona offline | ✅ | ✅ |
| Accesso camera | ✅ (HTTPS richiesto) | ✅ |
| Web Audio API | ✅ (richiede tocco utente) | ✅ |
| Icona Home Screen | ✅ | ✅ |
| Notifiche push | ❌ (iOS 16.4+ solo) | ✅ |
| Distribuzione App Store | ❌ | ✅ |
| Costo distribuzione | Gratuito | $99/anno |

---

## Nota MediaPipe (hand tracking)
MediaPipe Hands viene caricato da CDN `cdn.jsdelivr.net`.
Dopo la prima visita viene messo in cache dal service worker
e funziona anche senza connessione internet.

Il caricamento iniziale richiede ~5-10 secondi la prima volta.
