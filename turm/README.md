# Raketenturm

Ein Wettrennen für zwei Handys: Thilo und Opi klettern gleichzeitig einen Turm hinauf, jeder auf seinem eigenen Handy. Wer zuerst bei der Rakete ist, gewinnt. Unterwegs geht es nur mit der richtigen Farbe oder Form weiter. Der Turm ist wie beim C64-Klassiker Nebulus gebaut: Wege und Treppen winden sich außen herum, die Figur läuft von selbst. An jeder Station wartet ein kleines Comic-Alien in einer Farbe und Form:

- **Farbmonster** mit der gleichen Farbe abschießen,
- **Türen** mit dem passenden Schalter öffnen (sie führen durch den Turm),
- **Aufzüge** mit dem passenden Knopf nach oben schicken.

Das aktuelle Ziel leuchtet, oben zeigt eine Zielkarte dasselbe Zeichen. Man tippt unten im Steuerpult den gleichen Knopf. Thilos Figur ist **Wabbel**, ein wackeliges Puddingmonster mit Propellermütze. Opi spielt einen Wabbel mit Schiebermütze, Brille und Schnurrbart.

Über einen eingebauten Sprachchat können die beiden beim Spielen miteinander reden. Mit **Allein üben** geht es auch ohne zweites Handy.

## Auf GitHub Pages veröffentlichen

1. Auf github.com ein neues **öffentliches** Repository anlegen, z. B. `raketenturm`.
2. **Add file → Upload files**, `index.html` (und diese `README.md`) hochladen, **Commit changes**.
3. **Settings → Pages**: unter *Build and deployment* als Source **Deploy from a branch** wählen, Branch **main**, Ordner **/ (root)**, **Save**.
4. Nach ein bis zwei Minuten läuft das Spiel unter `https://BENUTZERNAME.github.io/raketenturm/`.

Tipp: Auf dem Handy die Seite über das Teilen-Menü **zum Home-Bildschirm hinzufügen**. Dann startet sie wie eine App.

## So wird gespielt

1. **Einmalig:** Beim ersten Öffnen fragt jedes Handy, wer darauf spielt. Auf Thilos Handy **Thilo** tippen, auf Opis Handy **Opi**. Das Handy merkt sich das. Beim ersten Mal fragt es außerdem nach dem Mikrofon (für den Sprachchat).
2. Danach öffnen beide einfach das Spiel und tippen **Los geht's!**. Die Handys finden sich von selbst, sobald beide online sind – egal, wer zuerst da ist. Kein Code, kein Link.
3. Sobald oben „Thilo ist da · Ton an“ steht, tippt Opi **Rennen starten**. Auf beiden Handys zählt es 3 – 2 – 1 – Los!
4. Beide Figuren laufen los und halten an jeder Station. Links zeigt eine **Rennleiste**, wie hoch beide gerade sind.
5. Wer zuerst oben ist, bekommt einen Pokal. Der andere klettert trotzdem bis zur Rakete. Danach startet Opi mit **Noch ein Rennen** die Revanche. Die Pokale werden gezählt, solange die Seite offen ist.

## Damit Thilo echte Chancen hat

Jedes Handy hat eigene Einstellungen. Beide Türme haben dieselben Stationen in derselben Reihenfolge, aber jeder bekommt seine eigenen Aufgaben.

- **Opi** bekommt von Anfang an schwerere Aufgaben (Farbe + Form mit 4 Knöpfen) und eine **langsamere Figur**. Das Tempo stellt man in Opis Einstellungen ein: Normal, Langsamer (Standard) oder Ganz langsam.
- **Thilo** bekommt die Aufgaben, die gerade dran sind, z. B. Farben mit 3 Knöpfen. Das stellt man auf Thilos Handy ein.
- Gewinnt Opi zu oft: Opis Figur eine Stufe langsamer stellen oder Opi mehr Knöpfe geben. Gewinnt Thilo immer mühelos: umgekehrt.

## Einstellungen (für Erwachsene)

Im Raum (Opi) und beim Warten (Thilo) über **Einstellungen**, im Spiel durch **eine Sekunde Gedrückthalten** des Menüknopfs oben rechts. So öffnet Thilo sie nicht aus Versehen.

- **Was wird geübt:** Farben, Formen, Formen bunt (nur die Form zählt), Farbe + Form.
- **Knöpfe:** 2, 3 oder 4 zur Auswahl.
- **Farben und Formen:** einzeln auswählen.
- **Tempo von Opis Figur** (nur auf Opis Handy): der Ausgleich im Rennen.
- **Stationen und Turmhöhe** (nur auf Opis Handy, gilt für beide): Farbmonster, Türen, Aufzüge; 5, 8 oder 12 Stationen.
- **Ruhiger Modus:** weniger Effekte; beim Allein-Üben auch langsamer.
- **Lernprotokoll:** zeigt, was beim ersten Versuch klappte.
- **Neues Rennen** (Opi) startet sofort ein neues Rennen, z. B. wenn die Verbindung lange weg war. **Zum Start** beendet die Verbindung.

## Anpassen

Oben in `index.html` im Block `CFG` lassen sich die Namen (`kind`, `begleiter`) ändern. Die Farben der Spielwelt stehen im Objekt `PAL`.

`raum` ist der feste Raum, in dem sich Thilos und Opis Handy treffen. Er ist zufällig gewählt. Soll eine andere Familie das Spiel nutzen, bekommt sie eine eigene Kopie mit einem anderen Raumnamen (nur Kleinbuchstaben und Ziffern), sonst landen alle im selben Raum.

Wer auf einem Handy spielt, lässt sich auf dem Startbildschirm über „Auf diesem Handy spielt nicht …?“ ändern.

## Technik

- Eine einzige HTML-Datei, keine Installation, keine Anmeldung.
- Die Verbindung zwischen den Handys läuft direkt von Handy zu Handy (WebRTC). Für den Verbindungsaufbau lädt die Seite die freie Bibliothek PeerJS und nutzt deren kostenlosen Vermittlungsserver. Dafür brauchen beide Handys Internet.
- **Allein üben** funktioniert auch ohne Internet, wenn die Seite einmal geladen ist.
- Bricht die Verbindung ab, klettert jeder einfach weiter. Thilos Handy sucht alle drei Sekunden nach Opis Handy, verbindet sich von selbst neu und trägt das Ergebnis nach.
- Jedes Handy nimmt nur Verbindungen vom Partner-Handy an. Fremde Verbindungen werden abgelehnt. Der Raumname steht allerdings in der Datei; wer das öffentliche GitHub-Repository liest, könnte ihn sehen. Wer das vermeiden möchte, ändert ihn ab und zu.
- Einstellungen werden auf dem jeweiligen Handy gespeichert. Es werden keine Spieldaten auf einem Server gespeichert.

## Kein Ton oder keine Verbindung?

- Lautstärke am Handy hochdrehen.
- Erscheint oben ein Lautsprecher-Knopf, einmal antippen. Dann ist der andere zu hören.
- Der Mikrofon-Knopf oben links schaltet das eigene Mikrofon stumm und wieder an.
- Kommt keine Verbindung zustande, beide Seiten neu laden. Steht oben „Ist Thilo noch auf einem anderen Gerät offen?“, läuft das Spiel mit derselben Rolle noch in einem anderen Tab oder auf einem anderen Handy – dort schließen. In manchen Firmen- oder Schul-WLANs ist die direkte Verbindung gesperrt; dann mit mobilen Daten versuchen.
- Nach dem Hochladen einer neuen Version die Seite einmal neu laden, damit das Handy nicht die alte Fassung aus dem Speicher zeigt.
