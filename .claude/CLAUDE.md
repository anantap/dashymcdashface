# dashymcdashface

Persoonlijk familiëdashboard als statische HTML-app.

## Projectstructuur

- `index.html` — de volledige applicatie (HTML, CSS, JS in één bestand)
- `SETUP.md` — instructies voor API-koppelingen en deployment

## Stack

- Puur statisch: geen build-stap, geen npm, geen framework
- Deployment via GitHub Pages of Vercel
- Weer: open-meteo API (geen key nodig)
- Agenda/mail: Google Calendar & Gmail API (OAuth2)

## Wijzigingen doorvoeren

Bewerk alleen `index.html`. Er is geen build-process; wijzigingen zijn direct zichtbaar.

## Deployment

Na pushen naar `main` wordt automatisch gedeployed via de geconfigureerde hosting (GitHub Pages of Vercel).
