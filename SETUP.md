# Google Cloud instellen — Persoonlijk Dashboard

## Wat ga je doen?
Een gratis Google Cloud project aanmaken zodat het dashboard toegang krijgt
tot jouw Google Calendar en Gmail. Dit kost ~5 minuten.

---

## Stap 1 — Google Cloud project aanmaken

1. Ga naar **https://console.cloud.google.com**
2. Klik bovenaan op het project-dropdown → **New Project**
3. Naam: `Persoonlijk Dashboard` → **Create**
4. Zorg dat het nieuwe project geselecteerd is

---

## Stap 2 — APIs inschakelen

1. Ga naar **APIs & Services → Library**
2. Zoek **Google Calendar API** → **Enable**
3. Zoek **Gmail API** → **Enable**

---

## Stap 3 — OAuth consent screen

1. Ga naar **APIs & Services → OAuth consent screen**
2. Kies **External** → **Create**
3. Vul in:
   - **App name**: `Dashboard`
   - **User support email**: jouw Gmail-adres
   - **Developer contact**: jouw Gmail-adres
4. Klik door: **Save and Continue** (3×) → **Back to Dashboard**
5. Klik op **Publish App** → **Confirm**
   *(anders kun je na 7 dagen niet meer inloggen)*

---

## Stap 4 — OAuth Client ID aanmaken

1. Ga naar **APIs & Services → Credentials**
2. Klik **+ Create Credentials → OAuth client ID**
3. Application type: **Web application**
4. Naam: `Dashboard`
5. Under **Authorized JavaScript origins**, voeg toe:
   - `https://JOUWGEBRUIKERSNAAM.github.io`
   - `http://localhost` *(voor lokaal testen)*
6. Klik **Create**
7. Kopieer de **Client ID** (ziet eruit als `xxxxx.apps.googleusercontent.com`)

---

## Stap 5 — Client ID in de HTML zetten

Open `index.html` en zoek deze regel bovenaan:

```javascript
GOOGLE_CLIENT_ID: 'YOUR_GOOGLE_CLIENT_ID',
```

Vervang `YOUR_GOOGLE_CLIENT_ID` met jouw gekopieerde Client ID:

```javascript
GOOGLE_CLIENT_ID: '123456789-abcdef.apps.googleusercontent.com',
```

---

## Stap 6 — GitHub Pages instellen

1. Maak een nieuwe GitHub repo aan: `dashboard` (of een andere naam)
2. Upload `index.html` als de enige file
3. Ga naar **Settings → Pages**
4. Source: **Deploy from branch → main → / (root)**
5. Je dashboard is live op: `https://JOUWGEBRUIKERSNAAM.github.io/dashboard/`

> Zorg dat deze URL overeenkomt met wat je in stap 4 hebt ingevuld
> bij **Authorized JavaScript origins**.

---

## Optioneel — Huckleberry bridge instellen

Als je thuis bent op hetzelfde netwerk als je PC Stick:

```javascript
HUCKLEBERRY_URL: 'http://192.168.1.XXX:POORT',
```

Voor toegang van buitenaf kun je een Cloudflare Tunnel gebruiken
(gratis, geen port forwarding nodig):

```bash
# Op je PC Stick:
cloudflared tunnel --url http://localhost:POORT
# Geeft een tijdelijke URL zoals: https://xyz.trycloudflare.com
```

Voor een permanente tunnel: zie https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/

---

## Feeds aanpassen

In `index.html`, in het `CONFIG` blok:

```javascript
// Jouw subreddits:
SUBREDDITS: ['Netherlands', 'hardware', 'homelab'],

// Jouw RSS feeds:
RSS_FEEDS: [
  { name: 'NOS', url: 'https://feeds.nos.nl/nosnieuwsalgemeen' },
  { name: 'The Verge', url: 'https://www.theverge.com/rss/index.xml' },
],
```

Parcel RSS URL kun je direct invullen in het dashboard zelf —
die wordt onthouden in je browser.
