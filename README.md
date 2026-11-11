# Stratford Walks — MVP 0.1

A mobile-first, multilingual walking tour prototype for Stratford, Ontario.

## Features
- 7 clickable landmarks: Cooper Terminal → Downie Street → City Hall → Library → Perth County Courthouse → Shakespearean Gardens → Avon Boathouse
- Leaflet/OpenStreetMap map, with **user-supplied coordinates and a pedestrian routing preview (Valhalla)**
- English, Brazilian Portuguese, Spanish content
- On-device browser speech synthesis with Play/Stop (voice availability varies)
- GPS position and optional proximity prompts while the page is active (requires HTTPS or localhost, permission, good accuracy)
- PWA manifest, service worker, responsive mobile/desktop layout
- No user accounts, analytics, API keys, or backend

## Run locally
From this folder:

```bash
python3 -m http.server 8080
```

Open http://localhost:8080 in a browser. The map requires an internet connection to load Leaflet from unpkg and tiles from OpenStreetMap. If offline, the stop list and stories still work. Mobile GPS requires deployment to HTTPS (localhost is also secure).

## Publish free
Upload these files to a static host such as Cloudflare Pages (Direct Upload) or GitHub Pages. Once deployed, use the HTTPS URL to make a QR code. This ZIP itself is **not** a live public website.

## Important before public use
1. Validate all seven marker coordinates and entrances on site; they are approximations.
2. Replace dotted straight-line connectors with a surveyed safe walking route; current connectors are **not turn-by-turn directions**.
3. Fact-check and enrich all seven stories with reliable historical sources and local review. Current copy is original introductory prototype copy, not finished historical research.
4. Test speech voices and GPS on actual iPhone/Android devices. GPS tracking stops when browsers suspend the page.
5. Replace emoji cover art with owned or properly licensed photos; ensure attribution and permissions.
6. Respect OpenStreetMap tile usage policy and attribution before wider traffic.
7. Test screen readers, accessibility and offline states.

Independent project; not affiliated with the City of Stratford, Stratford Festival or Destination Stratford.


## v0.1.3 pedestrian route preview
The app requests a pedestrian route from the public Valhalla demo service on first load, then stores the resulting geometry in browser localStorage. A solid green line means a route was returned; dotted terracotta lines mean the service was unavailable. This public demo endpoint has no uptime guarantee and may enforce usage limits. The route and approximate landmark coordinates must be checked in person before tourist use. No key or paid service is required for this prototype.

## v0.1.4 coordinate update
Markers 1–7 now use coordinates supplied by project owner. The **Courthouse (stop 5)** and **Shakespearean Gardens (stop 6)** received identical coordinates (43.3715438, -80.9857614); this requires confirmation before publication. To make both numbered markers accessible in the meantime, they are visually offset a few pixels in opposite directions while both use their exact supplied geographic coordinates.

The pedestrian routing query omits redundant consecutive duplicate waypoints and caches the resulting geometry under a key incorporating all route coordinates, so older geometry is never silently reused. The service worker and asset versions were incremented. The calculated route remains a preview and must be verified in person.
