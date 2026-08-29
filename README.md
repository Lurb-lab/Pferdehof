# 🐴 Pferdehof – Das Wettlaufspiel

Ein kinderfreundliches, browserbasiertes Würfel-Wettlaufspiel im Pferde-Design.
Gebaut mit reinem HTML5, CSS3 und Vanilla JavaScript – keine Build-Tools, keine
Abhängigkeiten, läuft als einzelne Datei direkt im Browser.

**[▶️ Jetzt spielen](https://<dein-github-username>.github.io/<repo-name>/)**
*(Link aktivieren, sobald GitHub Pages eingerichtet ist, siehe unten)*

<p align="center">
  <img src="assets/icons/icon-512.png" width="120" alt="App-Icon">
</p>

## Spielidee

Vier Weiden mit je drei Pferden (Weiß, Braun, Grau, Schwarz) müssen gemeinsam
auf die Koppel gebracht werden, bevor der Affe auf der Gefahrenleiste sein
viertes und letztes Feld erreicht und das Gatter öffnet.

- 🎲 Auf den Würfel tippen zeigt eine Pferdefarbe, einen Joker (⭐) oder den Affen (🐒)
- Bei einer Farbe: passendes Pferd auf der Weide anklicken
- Beim Joker: ein beliebiges verbleibendes Pferd wählen
- Beim Affen: die Gefahrenleiste rückt automatisch ein Feld näher ans Gatter
- **Sieg:** alle 12 Pferde sind auf der Koppel
- **Niederlage:** der Affe erreicht das Gatter und öffnet es
- 📊 Eine Statistik unterhalb der Koppel zählt Siege, Niederlagen und
  abgebrochene Partien (gespeichert im Browser des Geräts)

## Lokal starten

Kein Build-Schritt nötig – einfach `index.html` im Browser öffnen, oder lokal servern:

```bash
python3 -m http.server 8000
# dann im Browser: http://localhost:8000
```

## Auf GitHub Pages veröffentlichen

1. Repo auf GitHub erstellen und diesen Ordner hochladen (siehe Befehle unten).
2. **Settings → Pages → Source:** `Deploy from a branch`, Branch `main`, Ordner `/root`.
3. Nach ein bis zwei Minuten ist das Spiel unter
   `https://<dein-github-username>.github.io/<repo-name>/` erreichbar.

```bash
git init
git add .
git commit -m "Initial commit: Pferdehof Wettlaufspiel"
git branch -M main
git remote add origin https://github.com/<dein-github-username>/<repo-name>.git
git push -u origin main
```

## Als installierbare Android-App verpacken (wie bei "Pegel – Niederschlagsbuch")

Gleicher Weg wie bei den anderen Projekten: über GitHub Pages + PWABuilder
(TWABuilder) zu einer installierbaren Android-App.

**1. Auf GitHub Pages veröffentlichen** (siehe Abschnitt oben), bis die Seite
   unter `https://<username>.github.io/<repo-name>/` erreichbar ist.
   → Wichtig: die Seite muss über **https** erreichbar sein, sonst erkennt
   PWABuilder sie nicht als installierbare PWA.

**2. PWA-Check machen:** [pwabuilder.com](https://www.pwabuilder.com) öffnen,
   die GitHub-Pages-URL eingeben, „Start" klicken. PWABuilder prüft `manifest.json`
   und den Service Worker (`sw.js`, hier bereits enthalten) automatisch und zeigt
   grüne Häkchen bei Manifest, Service Worker und Icons.

**3. Android-Paket erzeugen:** Im Tab „Android" auf „Generate Package" klicken.
   PWABuilder baut daraus eine TWA (Trusted Web Activity) – eine Android-App, die
   deine Website in einem app-ähnlichen, vollflächigen Fenster ohne Browser-Leiste
   öffnet.

   ⚠️ **Achtung Package-Name:** PWABuilder schlägt standardmäßig
   `io.github.lurb_lab.twa` vor – denselben Namen wie bei "Pegel" und
   "Baustelle". Für dieses Projekt im Android-Tab **einen eigenen, eindeutigen
   Package-Namen** vergeben (z. B. `io.github.lurb_lab.pferdehof`), sonst gibt
   es beim Installieren auf demselben Gerät einen Konflikt mit den anderen Apps.

**4. Download & Installation:**
   - Heruntergeladene `.apk`-Datei aufs Handy übertragen (oder direkt am Handy
     downloaden).
   - „Installation aus unbekannten Quellen" für den Downloads-Ordner/Browser
     einmalig erlauben.
   - APK antippen → installieren. Das Spiel erscheint danach als eigenes
     App-Icon auf dem Homescreen.

**5. Bekannte Stolpersteine** (aus Erfahrung mit den anderen Projekten):
   - Browser-natives `confirm()`/`alert()` wird in TWA-Kontexten teils blockiert
     – dieses Spiel nutzt bereits ein eigenes In-App-Overlay statt `confirm()`,
     das Problem sollte hier also nicht auftreten.
   - Nach Änderungen an Dateien (v. a. Umbenennungen) kann der TWA-Cache auf
     Android hängen bleiben. Hilft: in den Android-Einstellungen unter
     „Apps → [App-Name] → Speicher → Cache leeren", danach die App neu starten.
   - `manifest.json` und `sw.js` müssen exakt im Root der veröffentlichten Seite
     liegen (nicht in einem Unterordner) – hier bereits so eingerichtet.

**Alternative:** Falls dir GitHub Pages zu langsam aktualisiert oder du lieber
sofort testen willst, kannst du auch [Netlify Drop](https://app.netlify.com/drop)
nutzen – Ordner per Drag & Drop hochladen, sofort eine https-URL erhalten und
diese dann bei PWABuilder eintragen.

```
.
├── index.html              # komplettes Spiel (HTML + CSS + JS, Grafiken eingebettet)
├── manifest.json            # Web App Manifest (Icons, Name, Theme-Farbe)
├── sw.js                     # Service Worker für Offline-Fähigkeit / TWA
├── assets/
│   └── icons/                # App-Icon in allen benötigten Formaten/Größen
├── LICENSE
└── README.md
```

## Technik

- Reines Vanilla JavaScript, keine Frameworks oder externen Skripte
- Alle Pferde-, Affen- und Koppel-Grafiken sind als Base64-PNG direkt in
  `index.html` eingebettet – läuft komplett offline, keine externen Bilddateien
  nötig
- Einzige externe Ressource: Google Fonts (Bungee, Fredoka) für die Typografie
- Responsives Layout für Desktop und Mobile
- Sieg-/Niederlage-/Abbruch-Statistik wird lokal per `localStorage` im Browser
  gespeichert (kein Server, keine Übertragung von Daten)

## Lizenz & Hinweis

Der Code in diesem Repository steht unter der [MIT-Lizenz](LICENSE) und darf
frei verwendet, verändert und weiterverbreitet werden.

Dies ist ein eigenständiges, nicht-kommerzielles Hobby-/Lernprojekt. Es basiert
auf einer klassischen, nicht schutzfähigen Sammel-Würfel-Spielmechanik und
verwendet ausschließlich selbst erstellte bzw. eigens generierte Grafiken,
Texte und Namen. Es besteht keine Verbindung zu und keine Billigung durch
Dritte.
