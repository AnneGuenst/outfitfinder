# Outfit-Finder – Anne Günst Fotografie

Interaktives Tool zur Outfit-Beratung für Foto-Shooting-Kunden.

## Projektstruktur

```
outfit-finder/
├── api/
│   └── chat.js          ← Serverless Proxy (versteckt den API-Key)
├── public/
│   └── index.html       ← Das komplette Frontend-Tool
├── vercel.json          ← Vercel-Konfiguration
└── README.md
```

## Setup

### 1. GitHub

1. Neues Repository anlegen auf [github.com](https://github.com)
2. Diese Dateien hochladen (alle drei Ordner/Dateien)

### 2. Vercel

1. [vercel.com](https://vercel.com) → „Add New Project"
2. GitHub-Repository auswählen → „Import"
3. **Environment Variable eintragen:**
   - Key: `ANTHROPIC_API_KEY`
   - Value: dein Anthropic API-Key (von [console.anthropic.com](https://console.anthropic.com))
4. „Deploy" klicken

### 3. Eigene Domain (optional)

In Vercel unter **Settings → Domains** z.B. `outfits.anneguenst.de` eintragen.
Danach beim Domain-Anbieter einen CNAME-Eintrag auf `cname.vercel-dns.com` setzen.

## Kleiderschrank aktualisieren

Die Kleider-Daten befinden sich in `public/index.html` in der `WARDROBE`-Liste (ca. Zeile 580).
Jeder Eintrag hat folgende Felder:

```js
{
  id: 'w9',                          // eindeutige ID
  label: 'Name des Kleidungsstücks',
  color: 'Anzeigename der Farbe',
  colorKey: ['creme', 'beige', ...], // Farb-Keywords für Matching
  sizes: ['XS', 'S', 'M'],          // verfügbare Größen
  persons: ['Mama', 'Schwanger'],    // passend für welche Personen
  style: ['clean-elegant', ...],     // passende Stilrichtungen
  image: 'https://...',              // Foto-URL (oder null)
  icon: '👗',                        // Fallback-Icon wenn kein Foto
}
```

**Verfügbare Stil-IDs:** `clean-elegant` · `boho-natural` · `romantic-feminine` · `earth-outdoor` · `baby-kids` · `family`

## API-Key beschaffen

1. [console.anthropic.com](https://console.anthropic.com) → „API Keys" → „Create Key"
2. Key kopieren und in Vercel als Environment Variable eintragen
3. Kosten: ca. 0,01–0,02 € pro Suchanfrage
