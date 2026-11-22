# e-netz Installateurportal – Bitwarden-Fix

Userscript (Tampermonkey/Violentmonkey), das Passwortmanagern wie **Bitwarden** das automatische Ausfüllen im
[Installateurportal der e-netz Südhessen](https://www.e-netz-suedhessen.de/installateurportal/) ermöglicht.

## Problem

Die Portal-Startseite ist ein veraltetes HTML-`<frameset>`:

```html
<frameset>
  <frame src="/installateurportal/secure/portalaufgabe.jsf" id="vnb-portal-frame">
</frameset>
```

Die äußere Seite hat kein `<body>`, deshalb kann Bitwarden dort weder das Feld-Icon noch die Auswahlliste
(Inline-Menü) einblenden. Zusätzlich fehlen den Login-Feldern die `autocomplete`-Attribute.

## Lösung

Das Script

1. lädt den Frame-Inhalt (`/installateurportal/secure/portalaufgabe.jsf`) direkt als Hauptseite und
2. setzt `autocomplete="username"` / `autocomplete="current-password"` auf die Login-Felder.

## Installation

1. [Tampermonkey](https://www.tampermonkey.net/) in Chrome installieren.
2. In neueren Chrome-Versionen unter `chrome://extensions` bei Tampermonkey **„Nutzerscripts zulassen“**
   aktivieren (bzw. den Entwicklermodus).
3. Script öffnen und installieren:
   [enetz-installateurportal-bitwarden.user.js](https://raw.githubusercontent.com/mod42/enetz-installateurportal-bitwarden/main/enetz-installateurportal-bitwarden.user.js)

## Alternative ohne Script

Lesezeichen direkt auf
`https://www.e-netz-suedhessen.de/installateurportal/secure/portalaufgabe.jsf` setzen. Damit entfällt das
Frameset; die fehlenden `autocomplete`-Attribute ergänzt aber nur das Script.

## Lizenz

MIT
