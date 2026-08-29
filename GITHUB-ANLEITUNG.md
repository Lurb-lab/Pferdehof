# 🚀 Schritt-für-Schritt: Pferdehof auf GitHub veröffentlichen

Diese Anleitung führt dich komplett ohne Kommandozeile durchs Veröffentlichen –
alles nur über die GitHub-Webseite. Am Ende ist eine Web-URL, auf der das Spiel läuft.

---

## 1. GitHub-Konto erstellen (falls noch nicht vorhanden)

1. Gehe auf **[github.com](https://github.com)**.
2. Klicke oben rechts auf **„Sign up"**.
3. E-Mail-Adresse, Passwort und Benutzernamen eingeben, den Anweisungen folgen
   (E-Mail-Bestätigung nicht vergessen).

Hast du schon ein Konto: einfach einloggen und weiter zu Schritt 2.

---

## 2. Neues Repository erstellen

1. Oben rechts auf das **„+"**-Symbol klicken → **„New repository"**.
2. **Repository name:** z. B. `pferdehof-spiel` (keine Leerzeichen, Kleinbuchstaben
   und Bindestriche sind sicher).
3. **Description:** optional, z. B. „Würfel-Wettlaufspiel im Pferde-Design".
4. **Public** auswählen (muss öffentlich sein, damit GitHub Pages kostenlos
   funktioniert).
5. **Wichtig:** Häkchen bei „Add a README file" **nicht** setzen – wir bringen
   unsere eigene README mit.
6. Auf **„Create repository"** klicken.

Du landest jetzt auf einer fast leeren Repository-Seite mit einem Hinweis
„Quick setup" und einem Upload-Link.

---

## 3. Dateien hochladen

1. Die ZIP-Datei aus dem Chat (`pferdehof-repo.zip`) auf deinem Rechner
   **entpacken**. Du bekommst einen Ordner `repo` mit diesem Inhalt:
   ```
   index.html
   manifest.json
   sw.js
   README.md
   LICENSE
   assets/icons/...
   ```
2. Zurück auf der GitHub-Repository-Seite: Klick auf **„uploading an existing
   file"** (Link im Quick-Setup-Text) – alternativ oben auf **„Add file" →
   „Upload files"**.
3. **Alle Dateien und den kompletten `assets`-Ordner** aus dem entpackten
   `repo`-Ordner per Drag & Drop in das Browserfenster ziehen.
   → Wichtig: den **Inhalt** des `repo`-Ordners hochladen, nicht den Ordner
   `repo` selbst als Unterordner (sonst landet `index.html` in
   `repo/index.html` statt im Hauptverzeichnis, und GitHub Pages findet die
   Seite nicht).
4. Unten bei „Commit changes" kannst du eine kurze Nachricht eintragen, z. B.
   „Initial commit", dann auf **„Commit changes"** klicken.

Nach ein paar Sekunden siehst du alle Dateien im Repository aufgelistet.

---

## 4. GitHub Pages aktivieren

1. Im Repository oben auf den Reiter **„Settings"** klicken.
2. Im linken Menü ganz unten auf **„Pages"** klicken.
3. Unter **„Build and deployment" → „Source"**: `Deploy from a branch`
   auswählen (meist schon vorausgewählt).
4. Bei **„Branch"**: `main` auswählen, Ordner daneben auf `/ (root)` stellen.
5. Auf **„Save"** klicken.

GitHub baut die Seite jetzt automatisch. Das dauert meist **30–90 Sekunden**.

---

## 5. Live-Seite aufrufen

1. Auf derselben Settings → Pages-Seite neu laden (F5) – oben erscheint ein
   grüner Kasten: **„Your site is live at
   `https://<dein-username>.github.io/<repo-name>/`"**.
2. Link anklicken oder in einen neuen Tab kopieren → das Spiel sollte jetzt
   laufen. 🐴

Falls du eine **404-Fehlerseite** siehst: meist ist die Seite einfach noch am
Bauen – 1–2 Minuten warten und neu laden. Bleibt der Fehler, prüfe in Schritt 3,
ob `index.html` wirklich direkt im Hauptverzeichnis liegt (nicht in einem
Unterordner `repo/`).

---

## 6. Spätere Änderungen hochladen

Willst du später etwas am Spiel ändern (z. B. eine neue Version von mir):

1. Im Repository zur betroffenen Datei navigieren (z. B. `index.html`).
2. Auf das **Stift-Symbol** („Edit this file") oben rechts klicken, um sie
   direkt im Browser zu bearbeiten – **oder** einfach über „Add file →
   Upload files" die neue Version hochladen; GitHub erkennt gleichnamige
   Dateien automatisch als Aktualisierung und fragt vor dem Überschreiben nach.
3. Commit-Nachricht eintragen, **„Commit changes"** klicken.
4. GitHub Pages aktualisiert die Live-Seite automatisch innerhalb von etwa
   einer Minute – kein erneutes Einrichten nötig.

**Tipp:** Wenn die Seite nach einem Update im Browser noch die alte Version
zeigt, hilft meist ein Hard-Reload (`Strg/Cmd + Shift + R`) oder kurz warten,
bis der Service Worker (`sw.js`) den neuen Cache übernommen hat.

---

## Alternative: mit Git über die Kommandozeile

Falls du lieber mit Git arbeitest (z. B. für häufigere Updates), findest du
die entsprechenden Befehle in der `README.md` im Abschnitt
„Auf GitHub Pages veröffentlichen".

---

## Kurz-Checkliste

- [ ] GitHub-Konto vorhanden
- [ ] Neues **öffentliches** Repository erstellt (ohne README-Häkchen)
- [ ] Alle Dateien aus dem `repo`-Ordner ins Hauptverzeichnis hochgeladen
- [ ] Settings → Pages → Branch `main` / `root` → Save
- [ ] Grüner „Your site is live"-Hinweis abgewartet
- [ ] Link geöffnet und Spiel getestet
