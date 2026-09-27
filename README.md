# Monochord

Web-App zum Entwerfen eigener Tonsysteme nach dem Prinzip des pythagoreischen
Quintenzirkels – mit frei wählbarem Intervall. Alles steckt in einer einzigen
Datei: [`index.html`](index.html). Keine Installation, kein Internet nötig.
Gedacht für das Handy im Hochformat.

## Starten

- `index.html` im Browser öffnen.
- Aufs Handy: z. B. GitHub Pages einschalten (Settings → Pages → Branch `main`,
  Ordner `/`) und die Seite dann in Safari über „Teilen → Zum Home-Bildschirm“
  als App ablegen.
- iPhone: Stummschalter bzw. Stumm-Modus ausschalten, sonst bleibt es still.

## Was die App kann

- **Monochord**: Saite mit verschiebbarem Steg. Die ganze Saite klingt als A
  (Stimmton 400–480 Hz, Standard 440 Hz). Stegposition als Prozent (zwei
  Nachkommastellen) oder als Bruch, Standard exakt 2/3. Antippen von „Teil“
  oder „Ganze Saite“ spielt den Ton.
- **Zirkel**: Die Stegposition wird immer wieder angewendet; Längen unter 50 %
  werden verdoppelt. Die App schlägt Schrittzahlen (2–60) vor, bei denen der
  nächste Ton dem A besonders nahe kommt (bei 2/3: 12, 41, 53). Ein Kreis zeigt
  die Reihenfolge der Entstehung, wahlweise nach Tonhöhe oder nach Reihenfolge.
- **Klaviatur**: Die Töne einer Oktave (ohne oberes A), sortiert nach Tonhöhe.
  Bei 12 Tönen nahe den Klaviertasten als klassische Klaviatur, sonst als Reihe
  gleich breiter Tasten, die über eine Leiste geblättert wird. Jede Taste zeigt
  Frequenz, Saitenlänge und nächste Klaviernote mit Abweichung in Cent.
  Multitouch und Glissando. Tasten lassen sich ausblenden, um Tonleitern zu bilden.
- **Klang**: gezupfte Saite (Karplus-Strong) oder Sinuston, Lautstärkeregler.
- **Speichern & Export**: Zirkel unter Namen speichern und laden, Export als
  Scala-Datei (`.scl`) plus Tastatur-Zuordnung (`.kbm`), damit A4 im Synthesizer
  den Grundton mit dem gewählten Stimmton spielt. Sicherung aller Zirkel als JSON.
- Heller und dunkler Modus, deutsche oder internationale Notennamen.

## Rechenweg

- Alle Saitenlängen werden als exakte Brüche gerechnet (BigInt), auch bei
  Prozentangaben (66,67 % = 6667/10000).
- Vorschlag = Schrittzahl, deren nächster Ton näher am A (oder oberen A) liegt
  als bei jeder kleineren Schrittzahl, und zwar um weniger als 50 Cent.
- Die `.scl`-Datei enthält exakte Verhältnisse, solange Zähler und Nenner in
  32 Bit passen, sonst Cent-Werte mit sechs Nachkommastellen.
- Gespeichert wird im Browser (`localStorage`) des jeweiligen Geräts.
