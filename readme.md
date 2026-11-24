# totalScanX – Handbuch

Version 2026.11.24 · Copyright © Rainer Brell

totalScanX hilft blinden und sehbehinderten Menschen, gedruckte Texte mit einem Scanner zu erfassen, in Text umzuwandeln und als Dokument zu lesen, zu bearbeiten und zu speichern. Ein Dokument besteht aus Seiten; jede Seite hat einen Text und (optional) das gescannte Originalbild. Wie eine Seite erfasst und erkannt wird, bestimmt das aktive **Profil**.

Das Programm gibt keine Sprache aus. Dafür ist ein Screenreader wie NVDA gedacht, der den Text im Textfeld und die Statusleiste vorliest.

---

## Inhalt

Mit den Links springen Sie direkt zum Kapitel. Im Handbuch (F1) bewegt sich der Fokus dabei auf die Überschrift des Kapitels; der Screenreader liest dort weiter.

- [1. Voraussetzungen](#1-voraussetzungen)
- [2. Programmstart](#2-programmstart)
- [3. Das Hauptfenster](#3-das-hauptfenster)
  - [Nur-Lese- und Bearbeitungsmodus](#nur-lese--und-bearbeitungsmodus)
- [4. Seiten erfassen](#4-seiten-erfassen)
  - [Qualitätsmeldung bei unsicherer Erkennung](#qualitätsmeldung-bei-unsicherer-erkennung)
  - [Neu erkennen](#neu-erkennen)
- [5. Profile](#5-profile)
  - [Standard-Profile](#standard-profile)
  - [Profil-Einstellungen (Liste)](#profil-einstellungen-liste)
  - [Registerkarte „Erfassen“ (Strg+Tab wechselt die Registerkarte)](#registerkarte-erfassen-strgtab-wechselt-die-registerkarte)
  - [Registerkarte „Verarbeitung“](#registerkarte-verarbeitung)
- [6. Mehrseitenerfassung](#6-mehrseitenerfassung)
- [7. Dokumente und Dateien](#7-dokumente-und-dateien)
  - [Vorschlag für den Dateinamen](#vorschlag-für-den-dateinamen)
  - [In allen Dokumenten suchen (F7)](#in-allen-dokumenten-suchen-f7)
  - [Als Hörfassung speichern (F8)](#als-hörfassung-speichern-f8)
- [8. Bearbeiten](#8-bearbeiten)
- [9. Navigation und Lesezeichen](#9-navigation-und-lesezeichen)
- [10. Ansicht](#10-ansicht)
- [11. Schnellfunktionen und Scannertasten](#11-schnellfunktionen-und-scannertasten)
- [12. Einstellungen](#12-einstellungen)
  - [Lokale KI](#lokale-ki)
- [13. Handbuch, Über und Updates](#13-handbuch-über-und-updates)
- [14. Protokolldatei](#14-protokolldatei)
- [15. Scanner: WIA und TWAIN](#15-scanner-wia-und-twain)
- [16. Tastenübersicht](#16-tastenübersicht)
- [17. Was totalScanX (noch) nicht kann](#17-was-totalscanx-noch-nicht-kann)
- [18. Fehlersuche](#18-fehlersuche)
- [Änderungsverlauf](#änderungsverlauf)

---

## 1. Voraussetzungen

- Windows 10 oder 11.
- Ein Scanner, der sich über **WIA** (Windows-Bilderfassung) oder **TWAIN** meldet.
- Texterkennung: **Tesseract OCR**. Fehlt es, bietet das Programm vor dem ersten Scan an, es automatisch einzurichten (Internetverbindung nötig).
- Optional: lokale KI für das Profil „Erfassen mit KI“. Die Einrichtung erfolgt beim Programmstart oder später über Einstellungen > Lokale KI installieren.

Zum Starten genügt die Datei **totalScanX.exe**; eine Installation ist nicht nötig.

Neben der Programmdatei legt totalScanX bei Bedarf Ordner an, die zum Programm gehören und **nicht gelöscht** werden sollten: **OCRData** (Sprachdaten der Texterkennung), **ollama** (lokale KI mit ihren Modellen) und **nvda** (Hilfsdatei für die direkten NVDA-Ansagen). Wird einer davon gelöscht, lädt das Programm den Inhalt bei Bedarf erneut aus dem Internet.

## 2. Programmstart

1. Das Programm sucht angeschlossene Scanner über WIA und TWAIN.
2. Findet es keinen, erscheint die Meldung **„Kein Scanner gefunden“**. Sie nennt ausdrücklich, dass weder ein Scanner mit Windows-Treiber (WIA) noch ein TWAIN-kompatibler Scanner entdeckt wurde, und enthält eine kurze Prüfliste (Kabel, Einschalten, Transportsicherung, Treiber, andere Scanprogramme). Mit **Erneut suchen** wird neu gesucht, mit **Beenden** schließt sich das Programm.
3. Wurden mehrere Scanner gefunden und ist der zuletzt benutzte nicht darunter, fragt ein Auswahldialog nach. Der zuletzt benutzte Scanner wird sonst ohne Rückfrage verwendet. Scanner erscheinen mit ihrer Schnittstelle, zum Beispiel „LiDE 400 (WIA)“.
4. **Tesseract OCR:** Danach prüft das Programm, ob die Texterkennung Tesseract OCR installiert ist. Fehlt sie, erscheint ein Hinweis mit der Frage, ob sie jetzt installiert werden soll. Der Hinweis nennt, dass dafür **Administratorrechte** nötig sind: Windows zeigt dazu eine Meldung (Benutzerkontensteuerung), die Sie mit „Ja“ bestätigen müssen. Wählen Sie **Beenden** oder kann die Installation nicht durchgeführt werden, schließt sich das Programm, denn ohne Tesseract OCR kann totalScanX nicht arbeiten. Fehlen nur die Sprachpakete Deutsch und Englisch, werden sie automatisch geladen.
5. **Lokale KI:** Ist die lokale KI noch nicht installiert, fragt das Programm, ob sie installiert werden soll. Sie benötigt etwa 8 GB Speicherplatz; das Programm prüft vor der Frage, ob so viel frei ist, und nennt den freien Platz. Die Frage nennt die Vorteile gegenüber einer Online-KI (Ihre Dokumente bleiben auf Ihrem Computer, nach der Installation ist keine Internetverbindung nötig, kein Konto, keine Kosten) und den Nachteil, dass die Verarbeitung etwas länger dauern kann. Wählen Sie **Später**, startet das Programm trotzdem; die Frage kommt dann nicht mehr, und die KI lässt sich jederzeit über **Einstellungen > Lokale KI installieren** nachinstallieren. Ist zu wenig Platz frei, weist das Programm darauf hin.
6. **Scannertasten:** Hat der Scanner Tasten (WIA), fragt das Programm einmalig, ob sie mit Profilen belegt werden sollen, und öffnet bei „Belegen“ gleich die Auswahl. Die Belegung lässt sich später unter Einstellungen > Allgemeine Einstellungen > Scannertasten ändern.
7. Ist die automatische Update-Prüfung eingeschaltet und besteht eine Internetverbindung, prüft das Programm auf eine neuere Version (siehe Abschnitt 13).
8. Läuft der Screenreader NVDA und wurde noch nicht entschieden, fragt das Programm, ob es eine kleine Hilfsdatei laden soll, damit NVDA wichtige Meldungen direkt sprechen kann (siehe Abschnitt 12).
9. **totalScanX ist bereit:** Sind beim ersten Start alle Fragen beantwortet und alle Einrichtungen abgeschlossen, erscheint einmalig die Meldung „totalScanX ist bereit“. Sie nennt Ihren Scanner und das aktive Profil und fasst den Einstieg zusammen: Seite auflegen und mit der **Leertaste** oder **F4** erfassen, Esc bricht ab, Strg+Bild ab und Strg+Bild auf blättern, Strg+S speichert, Strg+E schaltet den Bearbeitungsmodus, Alt öffnet die Menüleiste, **F1** öffnet das Handbuch. Nach **OK** stehen Sie im Hauptfenster und können sofort erfassen. Die Meldung kommt danach nicht mehr von selbst; Sie finden sie jederzeit unter **Hilfe > Erste Schritte**.

Ist die Protokolldatei eingeschaltet (Einstellungen > Allgemeine Einstellungen, Standard: aus, oder Start mit dem Parameter `-log`), wird beim Start hineingeschrieben, welches Betriebssystem (32/64 Bit) läuft und welche Scanner über welche Schnittstelle gefunden wurden (siehe Abschnitt 14).

## 3. Das Hauptfenster

- **Textfeld** (Dokumenttext): zeigt den Text der aktuellen Seite.
- **Originalansicht**: das gescannte Bild der Seite (Strg+Umschalt+V wechselt hin und her).
- **Statusleiste** mit zwei Feldern. Links: „Seite 2 von 7“ (bei eigener Seitenzahl zusätzlich „Seitenzahl 10“). Rechts: Modus, Wörter, aktives Profil oder die letzte Meldung. Der Screenreader liest die Statusleiste mit seiner Statusleisten-Taste (NVDA: Einfügen+Ende).
- **Titelzeile**: Programmname, Dokumentname und ein Stern bei ungespeicherten Änderungen.

### Nur-Lese- und Bearbeitungsmodus

Das Programm startet im **Nur-Lese-Modus**: Der Text lässt sich lesen und markieren, aber nicht ändern, und die **Leertaste erfasst eine Seite**. Mit **Strg+E** wechseln Sie in den **Bearbeitungsmodus**. Dort gibt es Bearbeitungsfunktionen wie Ausschneiden, Einfügen, Seitenumbrüche und Ersetzen; die Leertaste schreibt ein Leerzeichen, erfasst wird dann nur mit F4. Soll das Programm immer im Bearbeitungsmodus starten: Einstellungen > Allgemeine Einstellungen.

## 4. Seiten erfassen

- F4 (im Nur-Lese-Modus auch Leertaste), Seite erfassen
- Strg+Umschalt+F4, Erfassen und aktuelle Seite ersetzen
- Menü Erfassen > Erfassen und neue Seite einfügen, neue Seite vor oder nach der aktuellen einfügen
- Menü Erfassen > Neu erkennen, Seite oder ganzes Dokument neu erkennen
- Alt+S, A (Menü Erfassen > Ausrichtung der eingelegten Seite prüfen), sagt an, wie die Seite im Scanner liegt
- Strg+Umschalt+Y, Spalten erkennen ein/aus (vorübergehend)
- Menü Erfassen > Doppelseite in zwei Seiten teilen, ein- oder ausschalten (vorübergehend)
- Strg+Umschalt+F3, Schnellvorschau (nur der obere Teil, eigenes Dokument)

Ablauf eines Scans: Das Programm sagt den Namen des Profils an, scannt, richtet die Seite automatisch aus (0/90/180/270 Grad), erkennt den Text und fügt die Seite ins Dokument ein. Während des Scans erscheint kein Dialog; das Programm arbeitet unsichtbar im Hintergrund und nimmt in dieser Zeit keine Eingaben an, außer **Esc: Das bricht die Erfassung ab**. Damit Sie hören, dass das Programm arbeitet, ertönt alle 3 Sekunden ein kurzer Arbeitston (wenn im Profil „Signalton beim Start und Arbeitston während der Erfassung“ eingeschaltet ist), und die Statusleiste zeigt den aktuellen Schritt. Dauert es länger als 15 Sekunden, etwa beim Profil „Erfassen mit KI“, sagt das Programm alle 15 Sekunden an, was gerade geschieht, zum Beispiel „Die KI schreibt den Text: 60 Prozent. Noch etwa 8 Sekunden.“ (Voraussetzung für die Ansage: direkte NVDA-Ansagen sind eingeschaltet). Ein laufender Scanvorgang des Geräts selbst wird noch zu Ende geführt, bevor der Abbruch wirkt. Am Ende ertönt ein Signal und die Statusleiste meldet das Ergebnis. Je nach Profil springt der Cursor auf die neue Seite oder bleibt an der alten Stelle.

Ist die gescannte Seite leer (zum Beispiel weil nichts aufliegt, auch bei offenem Deckel), sagt das Programm gleich nach dem Scan „Leere Seite.“, ohne erst Text zu erkennen oder die KI zu fragen. Bei einer einzelnen Seite wird dann nichts eingefügt. Im Mehrseitenmodus bleibt eine leere Seite (etwa in einem Buch) als leere Seite im Dokument, außer im Profil ist „Leere Seiten verwerfen“ eingeschaltet. Ist eine Seite nicht leer, aber es wird kein Text darauf erkannt (zum Beispiel nur ein Bild), wird sie eingefügt und das Programm sagt „Kein Text erkannt.“

„Ausrichtung der eingelegten Seite prüfen“ läuft genauso im Hintergrund: Das Programm sagt „Ausrichtung wird geprüft.“, scannt ohne Dialog (Esc bricht ab) und sagt am Ende, wie die Seite liegt: richtig ausgerichtet, auf dem Kopf oder seitwärts. Liegt keine Seite mit Text auf dem Scanner, sagt es das.

Tipp: Kleine Bücher quer auflegen und „Doppelseite in zwei Seiten teilen“ einschalten; dann werden beide Seiten getrennt abgelegt.

### Qualitätsmeldung bei unsicherer Erkennung

Liegt eine Seite schief, ist sie abgeschnitten oder schlecht gedruckt, entsteht oft unbrauchbarer Text. Damit Sie das nicht erst beim Zuhören merken, meldet das Programm nach der Texterkennung, wenn die Erkennung unsicher war, zum Beispiel: „Die Erkennung ist unsicher (Sicherheit 42 Prozent).“ Reicht Text bis an den Bildrand, kommt der Hinweis dazu, dass die Seite vermutlich abgeschnitten ist oder nicht ganz aufliegt.

Ist die lokale KI eingerichtet, fragt das Programm, ob sie die Seite neu lesen soll (Schaltflächen **Mit KI neu lesen** und **So lassen**). Die KI liest dann dasselbe gescannte Bild noch einmal; Sie müssen die Seite nicht neu auflegen. Das dauert etwa eine halbe Minute; Esc bricht ab, der bisherige Text bleibt dann erhalten. Ohne lokale KI und bei der Mehrseitenerfassung warnt das Programm nur und gibt den Tipp, die Seite gerade und vollständig aufzulegen. Das Verhalten lässt sich je Profil einstellen (Registerkarte „Verarbeitung“). Die Meldung gibt es nur bei der Texterkennung mit Tesseract, nicht bei „Erfassen mit KI“.

### Neu erkennen

Gefällt die Qualität nicht, kann die Seite (oder das ganze Dokument) aus dem gespeicherten Originalbild neu erkannt werden. Voraussetzung: Im Profil war „Gescanntes Bild zur Seite speichern (Originalansicht)“ eingeschaltet. Der bisherige Text der Seite wird ersetzt (Strg+Z macht das rückgängig). Für die Neuerkennung wirkt die vorübergehende Umschaltung „Spalten erkennen“. Erkannt wird mit dem aktiven Profil; das Programm sagt „Neu erkennen mit“ und den Namen des Profils an. Wie beim Erfassen erscheint kein Fortschrittsdialog: Der aktuelle Schritt steht in der Statusleiste, der Arbeitston läuft (wenn das Profil ihn vorsieht), bei längeren Vorgängen kommt alle 15 Sekunden eine Ansage, und Esc bricht ab.
## 5. Profile

Ein Profil ist eine Sammlung von Einstellungen zum **Erfassen** und **Verarbeiten**. Das aktive Profil wird in der Statusleiste genannt. Wechseln: Menü Erfassen > Profil. Verwalten: **Einstellungen > Profil-Einstellungen**.

### Standard-Profile

- **Erfassen und lesen**: Eine Seite erfassen, erkennen, ans Dokumentende anhängen, Cursor auf die neue Seite. Voreinstellung.
- **Erfassen mit KI**: Wie oben, aber die Erkennung übernimmt die lokale KI statt Tesseract.
- **Erfassen im Hintergrund**: Neue Seite wird angehängt, der Cursor bleibt an der aktuellen Lesestelle.
- **Nur Bild erfassen**: Scannt nur und speichert eine Bilddatei (TIFF, PNG, JPEG, BMP oder PDF), ohne Erkennung.
- **Postsortierungsvorschau**: Erfasst nur die oberen 30 Prozent, ohne Spaltenerkennung, ersetzt die aktuelle Seite. Gedacht für Briefumschläge.
- **Mehrseiten - Für jede Seite nachfragen**: Nach jeder Seite fragt ein Dialog: *Nächste Seite erfassen*, *Stapel umdrehen und Rückseiten erfassen* oder *Erfassung beenden*.
- **Mehrseiten - Automatisch**: Wartet zwischen den Seiten die eingestellte Zeit (0 bis 25 Sekunden) und erfasst von selbst weiter. Esc oder die Schaltfläche „Anhalten“ öffnet den Mehrseiten-Dialog.
- **Lyrik und Rezept**: Behält die Zeilenumbrüche des Originals bei.

Standard-Profile können geändert, aber nicht gelöscht oder umbenannt werden; geänderte erscheinen mit dem Zusatz „geändert“ und lassen sich über **Werkseinstellungen wiederherstellen** zurücksetzen. Dazu gibt es zwei **spezielle Profile** („Bilddatei erkennen“ und „PDF-Datei“), die beim Öffnen solcher Dateien benutzt werden; von ihnen lassen sich nur die Verarbeitungseinstellungen ändern.

### Profil-Einstellungen (Liste)

Die Liste zeigt alle Profile, das aktive mit „aktiv“. Schaltflächen: **Bearbeiten**, **Neu erstellen** (Kopie des gewählten Profils unter neuem Namen), **Als aktiv setzen**, **Umbenennen**, **Entfernen** (nur eigene, nicht aktive), **Werkseinstellungen wiederherstellen** (nur geänderte Standard-Profile).

### Registerkarte „Erfassen“ (Strg+Tab wechselt die Registerkarte)

- **Erfassungsmodus**: „Eine Seite“ oder „Mehrere Seiten nacheinander“. Bei mehreren Seiten: **Nach jeder Seite nachfragen** oder **Automatisch nach der Wartezeit** mit der **Wartezeit zwischen den Seiten** (0 bis 25 Sekunden). Diese beiden Felder sind gesperrt, solange „Eine Seite“ gewählt ist.
- **Farbmodus**: Farbe oder Graustufen.
- **Auflösung**: 200, 300, 400, 500 oder 600 dpi. 300 dpi reicht für normalen Druck; 400 dpi bei sehr kleiner Schrift, wenn der Scanner optisch so hoch auflöst.
- **Ganze Auflagefläche scannen** oder **Nur den oberen Teil scannen** (10 bis 90 Prozent von oben; das Feld ist gesperrt, solange die ganze Auflagefläche gescannt wird).
- **Namen des Profils ansagen, wenn der Scan beginnt** (so hören Sie, mit welchem Profil erfasst wird), **Signalton beim Start und Arbeitston während der Erfassung**, **Signalton, wenn der Scan fertig ist**, **Erfassten Text von NVDA vorlesen lassen** (nach der Meldung liest NVDA den Text; braucht die direkten NVDA-Ansagen; bei „Erfassen und lesen“ standardmäßig an).
- **Neue Seite einfügen**: am Ende des Dokuments anhängen, nach der aktuellen Seite, vor der aktuellen Seite oder die aktuelle Seite ersetzen.

### Registerkarte „Verarbeitung“

- **Erkennung**: Texterkennung (Tesseract), lokale KI oder nur Bild.
- **Standard-Erkennungssprachen verwenden** oder eigene erste und zweite Sprache (Deutsch, Englisch, Französisch, Spanisch, Italienisch, Niederländisch, Türkisch, Russisch, Polnisch, Portugiesisch). Fehlende Sprachpakete werden vor dem Scan zum Download angeboten. Für Deutsch lädt das Programm das ausführlichere Sprachpaket (etwa 15 MB), das auch schlechte Vorlagen (niedrige Auflösung, stark komprimierte Bilder) genauer liest; ein älteres kleines Deutsch-Paket wird beim Start automatisch ersetzt.
- **Gescanntes Bild zur Seite speichern (Originalansicht)** (nötig für „Neu erkennen“ und die Originalansicht).
- **Ansagen, wie die Seite im Scanner lag**, **Kleine Flecken entfernen (Entsprenkeln)** (für verschmutzte oder oft kopierte Vorlagen), **Leere Seiten verwerfen**.
- **Korrekturwörterbuch anwenden** (Wörterbuch aus Abschnitt 8).
- **Unsicher erkannte Wörter durch ein Zeichen ersetzen**: Wörter mit geringer Erkennungssicherheit werden durch das **Zeichen für unsichere Wörter** (Standard `*`) ersetzt. Das Feld für das Zeichen ist gesperrt, solange die Einstellung aus ist.
- **Wenn die Erkennung der ganzen Seite unsicher ist**: Das Programm kennt nach jeder Texterkennung deren Sicherheit. Liegt sie unter 60 Prozent, gilt die Seite als unsicher erkannt. Zur Wahl stehen: **Nachfragen, ob die lokale KI die Seite neu lesen soll** (Standard), **Seite automatisch mit der lokalen KI neu lesen**, **Nur warnen** und **Nichts tun**. Siehe „Qualitätsmeldung“ in Abschnitt 4.
- **Zeilenumbrüche beibehalten**: sonst werden Zeilen eines Absatzes zusammengezogen und Trennstriche aufgelöst.
- **Spaltenerkennung**: Spalten erkennen (Zeitungen) oder Spalten ignorieren (Rechnungen, Briefe über die ganze Breite).
- **Doppelseite in zwei Seiten teilen**.
- **Nach dem Erkennen**: zur neuen Seite springen oder an der aktuellen Lesestelle bleiben.

## 6. Mehrseitenerfassung

Bei den beiden Mehrseiten-Profilen (oder jedem Profil mit Erfassungsmodus „Mehrere“) erfasst das Programm Seite um Seite, bis Sie beenden.

**Stapel umdrehen und Rückseiten erfassen** hilft bei doppelseitigen Dokumenten: Erfassen Sie zuerst alle Vorderseiten (1, 3, 5), wählen Sie „Stapel umdrehen und Rückseiten erfassen“ und erfassen Sie dann die Rückseiten **in umgekehrter Reihenfolge** (6, 4, 2). Das Programm sortiert sie richtig ein. Erfassen Sie auch die Rückseite der letzten Seite, selbst wenn sie leer ist. Die Schaltfläche steht nicht zur Verfügung, wenn „Doppelseite in zwei Seiten teilen“ aktiv ist.

Endet die Erfassung mit einem Scannerfehler (zum Beispiel weil kein Papier mehr eingelegt ist), bleiben die bereits erfassten Seiten erhalten.

## 7. Dokumente und Dateien

Mehrere Dokumente können gleichzeitig geöffnet sein; **Strg+F6** schaltet zum nächsten um und nennt dessen Namen. Neue Dokumente heißen Namenlos, Namenlos2, …

- Strg+N, Neu
- Strg+O, Öffnen
- Menü Datei, Datei anhängen (Seiten werden ans Dokumentende gesetzt)
- Strg+F4, Schließen
- Strg+S, Speichern
- Menü Datei, Speichern unter
- Strg+Umschalt+S, Seiten speichern (aktuelle Seite oder Bereich wie `2-6` oder `2,3,4`)
- Strg+P, Drucken (Text über den Windows-Druckdialog)
- Menü Datei, Dokumenteigenschaften
- Menü Datei, Zuletzt geöffnet (die letzten fünf .tsx-Dateien)

**Dateiformate**

- **.tsx**: das eigene Format. Es enthält alle Seiten mit Text, Seitenzahlen, Lesezeichen und Originalbildern. Standardformat zum Speichern.
- **Export** (Datei > Speichern unter oder Seiten speichern, Auswahlliste „Dateityp“):
  - **Word-Dokument (.docx)**: der Text aller Seiten zum Weitergeben und Weiterbearbeiten. Jede Seite beginnt auf einer neuen Seite, Absätze bleiben erhalten, die Schrift ist Arial 12 Punkt, als Sprache ist Deutsch eingetragen. Bilder und Lesezeichen sind nicht enthalten.
  - **Durchsuchbares PDF (.pdf)**: Jede Seite zeigt das Originalbild, wie es gescannt wurde; darunter liegt unsichtbar der erkannte Text an der richtigen Stelle. Empfänger sehen das Schreiben im Original und können darin suchen, Text markieren und kopieren; ein Screenreader liest den Text vor. Die Textschicht erzeugt Tesseract OCR beim Speichern neu aus dem Originalbild (etwa zwei Sekunden je Seite). **Wichtig:** Ihre Korrekturen am Text und der Text aus „Erfassen mit KI“ stehen deshalb nicht in diesem PDF; wenn es auf den korrigierten Text ankommt, geben Sie das Word-Dokument weiter. Seiten ohne Originalbild werden als reine Textseiten mit Ihrem Text gesetzt. Esc bricht das Erstellen ab.
  - **Textdatei (.txt), RTF-Datei (.rtf), HTML-Datei (.html)**: nur der Text, ohne Bilder und Lesezeichen.
  - **PDF nur mit Originalbildern, ohne Text (.pdf)**: nur die Bilder der Seiten; nicht durchsuchbar und für Screenreader nicht lesbar. Nur möglich, wenn Originalbilder vorhanden sind.
- **Öffnen**: .tsx, .txt, .rtf, .pdf und Bilddateien (.png, .jpg, .bmp, .tif, .gif, .pcx). PDFs mit Textebene werden direkt übernommen, reine Bild-PDFs und Bilder werden per Texterkennung erkannt (mit den speziellen Profilen).

Beim Schließen eines Dokuments oder Beenden des Programms fragt totalScanX bei ungespeicherten Änderungen: **Speichern**, **Nicht speichern** oder **Abbrechen**. Das gilt auch vor einem Update.

Standardordner für Dateidialoge: Einstellungen > Allgemeine Einstellungen > Ordner für Ihre Dokumente (Voreinstellung: Dokumente\totalScanX).

### Vorschlag für den Dateinamen

Beim ersten Speichern eines neuen Dokuments schlägt das Programm einen Namen aus Datum, Absender und Art des Schreibens vor, zum Beispiel „2026-11-03 Stadtwerke Musterstadt GmbH Rechnung“. Das Datum steht vorn und in der Reihenfolge Jahr-Monat-Tag, damit die Dateien im Ordner nach Datum sortiert sind. Den Vorschlag gibt es nur, wenn im Text ein Datum oder eine Art (Rechnung, Mahnung, Bescheid …) gefunden wurde; sonst bleibt es beim bisherigen Namen. Sie können den Vorschlag im Feld „Dateiname“ jederzeit überschreiben. Haben Sie vorher „Brief auf einen Blick“ (F3) benutzt, werden dessen Angaben verwendet.

### In allen Dokumenten suchen (F7)

**Datei > In allen Dokumenten suchen** durchsucht alle gespeicherten Dokumente im Ordner für Ihre Dokumente samt Unterordnern, und zwar totalScanX-Dokumente (.tsx) und Textdateien (.txt). So finden Sie ein Schreiben wieder, ohne Papier oder Dateien einzeln durchzugehen.

1. Geben Sie unter **Suchen nach** ein oder mehrere Wörter ein und drücken Sie die Eingabetaste. Mehrere Wörter müssen alle auf derselben Seite stehen; Groß- und Kleinschreibung spielt keine Rolle.
2. Die Liste **Treffer** nennt je Treffer den Dateinamen, die Seite und die Textstelle. Neuere Dateien stehen oben. Das Programm zeigt höchstens 300 Treffer.
3. **Öffnen** (oder Eingabetaste in der Liste) öffnet das Dokument auf der Seite des Treffers und markiert das gefundene Wort.

### Als Hörfassung speichern (F8)

**Datei > Als Hörfassung speichern** spricht das Dokument mit einer Stimme von Windows und speichert es als Tondatei, die Sie auf dem Telefon oder einem Abspielgerät hören können.

- **Umfang**: ganzes Dokument oder aktuelle Seite.
- **Stimme**: alle in Windows installierten Stimmen; deutsche Stimmen stehen oben. Weitere Stimmen lassen sich in den Windows-Einstellungen unter Zeit und Sprache > Sprachausgabe hinzufügen. Eine Stimme kann zweimal erscheinen (klassisch mit dem Zusatz „Desktop“ und in der neueren Fassung). Die natürlichen Stimmen der Windows-Sprachausgabe stehen anderen Programmen nicht zur Verfügung und fehlen deshalb in der Liste.
- **Sprechtempo**: Langsam, Normal, Etwas schneller oder Schnell.
- **Vor jeder Seite die Seitenzahl ansagen**: hilft, sich in langen Dokumenten zurechtzufinden.

Danach wählen Sie Ordner, Namen und Format: **MP3** (klein, etwa 0,5 MB je Minute) oder **WAV** (unkomprimiert, etwa 5 MB je Minute). Es entsteht eine Datei für den gewählten Umfang. Stimme und Tempo merkt sich das Programm. Für MP3 wird der in Windows eingebaute Kodierer benutzt; es wird nichts zusätzlich installiert. Abbrechen im Fortschrittsdialog verwirft die unfertige Datei.

## 8. Bearbeiten

Die Bearbeitungsfunktionen brauchen den Bearbeitungsmodus (Strg+E), außer Kopieren, Markieren und Suchen.

- Strg+Z, Rückgängig (die letzte Seiten-Aktion oder Texteingabe)
- Strg+X, Ausschneiden
- Strg+C, Kopieren
- Strg+V, Einfügen
- Strg+A, Alles auf der aktuellen Seite markieren
- Strg+F, Text suchen (über alle Seiten)
- Strg+Umschalt+F, Weitersuchen
- Strg+H, Text ersetzen (einzeln oder „Alles ersetzen“)
- Strg+Eingabe, Seitenumbruch einfügen (teilt die Seite an der Cursorposition)
- Strg+Umschalt+Entf, Seitenumbruch löschen (verbindet die aktuelle mit der nächsten Seite)
- Strg+Entf, Aktuelle Seite löschen (mit Rückfrage)
- Menü Bearbeiten, Seite verschieben (nach oben/unten, Anfang, Ende, Zielseite oder relativ wie `+2`)
- Menü Bearbeiten, Seiten neu nummerieren
- Menü Bearbeiten, Kopf- und Fußzeilen entfernen
- Menü Bearbeiten, Wörter zählen
- Menü Bearbeiten, Korrekturwörterbuch
- F2, Mit KI bearbeiten

**Seiten neu nummerieren**: Die aktuelle Seite bekommt die eingegebene Zahl, alle folgenden werden fortlaufend weitergezählt. Die Zahl muss größer sein als die der vorherigen Seite. Mit dem Kontrollfeld „Auf Originalnummerierung zurücksetzen“ kehren Sie zur laufenden Nummerierung zurück. In „Gehe zu“ gilt die angezeigte Seitenzahl.

**Kopf- und Fußzeilen entfernen**: Entfernt je Seite die erste und/oder letzte nicht leere Zeile des Textes. Das Originalbild bleibt unverändert.

**Korrekturwörterbuch**: Ein Wörterbuch aus „falsch erkanntes Wort“ und „Korrektur“ (ganze Wörter, ohne Leerzeichen im falschen Wort; die Korrektur darf Leerzeichen enthalten), optional mit Beachtung der Groß-/Kleinschreibung. Es wird bei jedem Scan automatisch angewendet (Profil-Einstellung) und kann mit „Auf Dokument anwenden“ nachträglich auf das ganze Dokument angewendet werden.

**Brief auf einen Blick** (F3): Nennt die fünf wichtigsten Angaben eines Schreibens: **Absender, Datum, Art** (Rechnung, Mahnung, Bescheid, Werbung …), **Betrag** und **Frist**. Das Ergebnis erscheint in einem Fenster, zuerst als ein Satz („Rechnung von Stadtwerke Musterstadt GmbH vom 3.11.2026. Betrag 96,40 Euro. Frist 24.11.2026.“), darunter als Liste. Mit **Als neue Seite einfügen** oder **Kopieren** lässt es sich weiterverwenden. Ausgewertet wird das ganze Dokument.

Ist die lokale KI eingerichtet, liest sie das Schreiben (einige Sekunden). Zum Schutz vor erfundenen Angaben übernimmt das Programm Datum, Betrag, Frist und Absender der KI nur, wenn sie sich im Text wiederfinden; sonst steht dort „keine Angabe“. Ohne lokale KI arbeitet eine einfache Auswertung nach festen Mustern; sie findet weniger, ist aber sofort fertig. Bitte prüfen Sie wichtige Angaben wie Beträge und Fristen immer im Originaltext.

**Mit KI bearbeiten** (F2): Die lokale KI bearbeitet den bereits erkannten Text. Es wird nichts ins Internet gesendet. Voraussetzung ist die eingerichtete lokale KI (Einstellungen > Lokale KI installieren), wie bei dem Profil „Erfassen mit KI“.

1. Wählen Sie den **Umfang**: aktuelle Seite oder ganzes Dokument.
2. Wählen Sie die **Aufgabe**: kurz oder ausführlich zusammenfassen, Stichpunkte, in leichter Sprache erklären, wichtige Angaben herausziehen (Datum, Beträge, Fristen, Kontodaten, Telefonnummern …), eine Frage zum Text beantworten, ins Englische oder Deutsche übersetzen, Erkennungsfehler korrigieren oder eine eigene Anweisung ausführen. Bei „Frage“ und „Eigene Anweisung“ geben Sie im Feld darunter die Frage oder Anweisung ein. Als letzte Aufgabe steht Ihre **gespeicherte eigene Anweisung** zur Wahl (Standardname „Gespeicherte eigene Anweisung“); Name und Text legen Sie unter Einstellungen > Allgemeine Einstellungen auf der Registerkarte „KI-Anweisungen“ fest. Auch den Wortlaut aller anderen Aufgaben können Sie dort ändern.
3. Mit „Starten“ beginnt die KI. Ein Fortschrittsdialog zeigt Prozent und Restzeit; „Abbrechen“ beendet die Aufgabe.
4. Das Ergebnis erscheint in einem eigenen Fenster als Webseite: Überschriften, Aufzählungen, Tabellen und Hervorhebungen, die die KI setzt, werden als solche angezeigt, und Sie lesen sie mit dem Lesemodus des Screenreaders wie eine Internetseite (bei NVDA zum Beispiel mit H zur nächsten Überschrift und L zur nächsten Liste). Mit Tab erreichen Sie die Schaltflächen: „Als neue Seite einfügen“ übernimmt das Ergebnis hinter der aktuellen Seite in das Dokument, „Kopieren“ legt es in die Zwischenablage. In beiden Fällen wird reiner Text ohne Auszeichnungszeichen übernommen; Aufzählungen beginnen mit einem Spiegelstrich. Übersetzungen und korrigierter Text werden unverändert angezeigt und übernommen. Ihr Originaltext wird nie verändert.

Dauer auf einem Rechner ohne starke Grafikkarte: kurze Fragen etwa 5 Sekunden, eine Zusammenfassung einer Seite etwa 10 Sekunden, die Übersetzung einer halben Seite etwa 25 Sekunden. **Mehrere Seiten auf einmal:** Beim Zusammenfassen, bei Stichpunkten, Fragen und beim Herausziehen von Angaben liest die KI bis etwa 5000 Wörter (rund zehn Seiten) am Stück; gemessen wurde für 4300 Wörter etwa eine Minute. Noch längere Texte werden in Teilen gelesen und dauern länger (6700 Wörter: gut zwei Minuten). Beim Übersetzen und beim Korrigieren von Erkennungsfehlern ist die Antwort so lang wie der Text; dort wird ab etwa 2200 Wörtern in Teilen gearbeitet, und das Ergebnis wird zusammengesetzt. Der Fortschrittsdialog zeigt den Gesamtfortschritt und die geschätzte Restzeit für die ganze Aufgabe. Auszeichnungen der KI (zum Beispiel Sternchen für Fettschrift und Aufzählungen) erscheinen nicht als Zeichen, sondern als Formatierung der Webseite; der Screenreader liest daher keine Sternchen vor.

**Wichtig:** Die KI kann sich bei Zahlen, Namen und Daten irren oder etwas falsch zusammenfassen. Prüfen Sie wichtige Angaben, zum Beispiel Beträge und Fristen, immer im Originaltext. Das Ergebnisfenster weist darauf hin.

## 9. Navigation und Lesezeichen

Zum Blättern gibt es im Menü Navigation das Untermenü „Seite wechseln“ mit den Einträgen Erste Seite, Letzte Seite, Vor (nächste Seite) und Zurück (vorherige Seite). Schneller geht es mit den Tasten:

- Strg+Bild ab, nächste Seite
- Strg+Bild auf, vorherige Seite
- Strg+Umschalt+Bild ab, letzte Seite
- Strg+Umschalt+Bild auf, erste Seite
- Strg+G, Gehe zu (Seite oder Lesezeichen)
- F9, Lesezeichen verwalten (hinzufügen, umbenennen, löschen, hingehen; sortiert nach Name oder Ort)
- Strg+F9, Lesezeichen an der Cursorposition einfügen

Lesezeichen merken sich Seite und Textposition. Wird der Text davor stark geändert, kann die Position leicht abweichen.

## 10. Ansicht

- Strg+Umschalt+V, Zwischen Text- und Originalansicht wechseln
- Strg+Umschalt+R, Bild nach rechts drehen
- Strg+Umschalt+Q, Bild nach links drehen (auch Strg+Umschalt+L, falls nicht von einem anderen Programm belegt)
- Strg+Plus, Zoom größer (Haupttastatur, auch mit Umschalt, und Ziffernblock)
- Strg+Minus, Zoom kleiner
- Strg+Umschalt+W, Auf Seitenbreite zoomen

Die Originalansicht gibt es nur für Seiten mit Originalbild. In der Originalansicht scrollen Sie mit den Pfeiltasten und Bild auf/ab.

## 11. Schnellfunktionen und Scannertasten

Die früheren Schnelltasten F5 bis F8 gibt es nicht mehr; alles läuft einheitlich über die **Profile** (Erfassen > Profil wählen, F4 erfasst mit dem aktiven Profil).

Scannertasten: Bei WIA-Scannern liest das Programm aus dem Treiber, welche Tasten der Scanner hat (zum Beispiel Scannen, Kopieren/Drucken, E-Mail, Fax, OCR). Jeder Taste lässt sich ein **Profil** zuordnen; ein Tastendruck am Scanner erfasst dann direkt mit diesem Profil und seinen Einstellungen. Zur Auswahl stehen dieselben Profile wie im Menü Erfassen > Profil, dazu „(keine Belegung)“. Beim Programmstart fragt totalScanX einmalig pro Scanner, ob die Tasten belegt werden sollen. Später ändern Sie die Belegung unter **Einstellungen > Allgemeine Einstellungen** auf der Registerkarte **Scannertasten**. Welche physische Taste gedrückt wurde, kann Windows nicht unterscheiden, nur ihre Art. Bei TWAIN-Scannern gibt es keine Tastenüberwachung. Die früheren festen Tastenbelegungen aus dem Assistenten sind entfallen.

## 12. Einstellungen

- **Allgemeine Einstellungen** (vier Registerkarten, Strg+Tab wechselt):
  - **Allgemein**: Ordner für Ihre Dokumente, Start im Bearbeitungsmodus, automatische Updates, Protokolldatei, Ansagen über NVDA, erste und zweite Erkennungssprache.
  - **KI-Anweisungen**: die Anweisungen, die „Mit KI bearbeiten“ (F2) an die lokale KI gibt. Wählen Sie unter **Aufgabe** einen Eintrag und ändern Sie die **Anweisung an die KI**; mit **Auf Standard zurücksetzen** kehrt der Eintrag zum ursprünglichen Wortlaut zurück. Bei „Frage zum Text beantworten“ und „Eigene Anweisung“ steht `%s` für die Eingabe, die Sie im F2-Dialog machen; fehlt `%s`, wird die Eingabe hinten angehängt. Der letzte Eintrag ist eine **gespeicherte eigene Anweisung**: Sie geben ihr einen Namen (erscheint in der Aufgabenliste von F2) und schreiben die Anweisung selbst. Sie wirkt auf den gewählten Text (Seite oder Dokument). Ist sein Text leer, weist F2 darauf hin. Geändert wird erst nach OK.
  - **Scannertasten**: Für jede Taste, die Ihr Scanner meldet, wählen Sie ein Profil oder „(keine Belegung)“ (siehe Abschnitt 11). Meldet der Treiber keine Tasten, werden die üblichen Tastenereignisse trotzdem überwacht. Bei TWAIN-Scannern gibt es keine Tasten.
  - **Töne**: Hier stellen Sie ein, wie die Töne der Erfassung klingen: der **Startton** (die Erfassung beginnt), der **Arbeitston** (wiederholt sich während der Erfassung) und der **Fertigton** (der Scan ist fertig). Für jeden Ton gibt es die Tonhöhe in Hertz (100 bis 4000, höhere Zahl = höherer Ton), die Länge in Millisekunden (20 bis 1000) und eine Schaltfläche zum Anhören. Beim Arbeitston stellen Sie zusätzlich den **Abstand in Sekunden** ein (1 bis 30, Standard 3). „Alle Töne auf Standard zurücksetzen“ stellt die ursprünglichen Werte wieder her (Startton 600 Hertz, Arbeitston 450 Hertz, Fertigton 900 Hertz, je 70 Millisekunden, Abstand 3 Sekunden). Ob ein Ton überhaupt gespielt wird, bestimmt weiterhin das Profil.
- **Profil-Einstellungen**: siehe Abschnitt 5.
- **Geräteauswahl**: Scanner (und Schnittstelle) wählen. Der Scanner wird gemerkt.
- **Lokale KI installieren**: Lädt die lokale KI (etwa 8 GB), falls sie noch nicht oder nicht vollständig eingerichtet ist, und prüft vorher den freien Platz. Fehlt nur eines der beiden Modelle, wird nur dieses nachgeladen (dann genügen 5 GB). Ist sie schon vorhanden, meldet das Programm das nur. Tesseract OCR wird beim Programmstart eingerichtet.
- **Beim Start nach Updates suchen** (Allgemeine Einstellungen, Registerkarte Allgemein): ein- oder ausschalten.
- **Protokolldatei totalScanX.log schreiben**: Standard ist aus. Eingeschaltet schreibt das Programm Start, Scans, Dateivorgänge und Fehler in die Protokolldatei (siehe Abschnitt 14). Gilt sofort.
- **Wichtige Meldungen direkt über NVDA sprechen**: Mit dem Screenreader NVDA sagt totalScanX dann Meldungen sofort an und zeigt sie auf der Braillezeile, zum Beispiel „Seite 3 von 12“ beim Blättern mit Strg+Bild auf/ab, „Bearbeitungsmodus“ / „Nur-Lese-Modus“ bei Strg+E, „Originalansicht“ / „Textansicht“, „Bild nach rechts gedreht“, „Zoom 125 Prozent“ (auch „Größter Zoom erreicht“), „Auf Seitenbreite gezoomt, Zoom 76 Prozent“ sowie Meldungen wie „Seite gelöscht“. Dafür braucht das Programm den **NVDA Controller Client** von NV Access (kleine Datei, etwa 4,5 MB Download, Lizenz LGPL 2.1). Er wird nur nach Ihrer Zustimmung aus dem Internet geladen und neben dem Programm im Ordner „nvda“ gespeichert. Beim Programmstart fragt totalScanX einmal danach, wenn NVDA läuft. Antworten Sie mit „Nein“, wird das gemerkt und nicht erneut gefragt; Sie können es hier jederzeit nachholen (Kontrollfeld einschalten, die Datei wird dann geladen). Ausschalten stellt die Ansagen wieder ab. Läuft NVDA nicht, geschieht nichts. Die Statuszeile wird weiterhin gefüllt.

Alle Einstellungen werden in `%APPDATA%\totalScanX\settings.json` gespeichert.

### Lokale KI

Für „Erfassen mit KI“ lädt das Programm auf Wunsch eine lokale KI-Software in den Unterordner `ollama` des Programmordners und zwei Modelle: **glm-ocr** (rund 2 GB) liest die gescannte Seite, **gemma4:e2b** (rund 4,5 GB) bearbeitet Text für „Mit KI bearbeiten“ (F2) und „Brief auf einen Blick“ (F3). Insgesamt werden dafür etwa 8 GB Speicherplatz benötigt. Das Programm prüft zuerst, ob am Zielort mindestens 8 GB frei sind; ist das nicht der Fall, meldet es den tatsächlich freien Platz und lädt nichts. Erst danach kommt die Rückfrage, die den Bedarf und den freien Platz nennt. Wer die KI schon hatte, wird beim Start einmal gefragt, ob das fehlende Modell nachgeladen werden soll (dafür genügen 5 GB). Ein früher geladenes Textmodell bleibt dabei im Ordner `ollama` liegen; das Programm benutzt es nicht mehr. Die KI liest das Bild und gibt den Text aus. Während der Verarbeitung zeigt ein Dialog Prozent und geschätzte Restzeit; das erste Mal dauert länger, weil das Modell geladen wird.

## 13. Handbuch, Über und Updates

- **Handbuch** (F1): zeigt dieses Handbuch als Webseite im Programmfenster. Das Handbuch ist in der Programmdatei enthalten; eine zusätzliche Datei ist nicht nötig. Mit Strg+Bild auf/ab, Pfeiltasten oder dem Lesemodus des Screenreaders navigieren Sie durch die Überschriften und Listen; Esc schließt.
- **Erste Schritte**: zeigt die kurze Einstiegshilfe mit Scanner, aktivem Profil und den wichtigsten Tasten, die nach dem ersten Start einmalig als Meldung „totalScanX ist bereit“ erscheint.
- **Über**: Programmname, Versionsnummer und Copyright. Die Versionsnummer ist das Datum der letzten Änderung im Format JJJJ.MM.TT.
- **Nach Updates suchen**: prüft die Veröffentlichungen auf GitHub (https://github.com/nvda-nachhaltig/totalScanX/releases). Gibt es eine neuere Version, fragt das Programm, ob es sie herunterladen und installieren soll. Vorher werden ungespeicherte Dokumente abgefragt. Dann lädt es die neue Programmdatei (Esc bricht ab), beendet sich, ersetzt die Programmdatei und startet neu. Das dauert nach dem Beenden einige Sekunden. Die neue Version steht dort auch zum Herunterladen von Hand bereit: unter „Assets“ die Datei totalScanX.exe.

## 14. Protokolldatei

Das Programm schreibt standardmäßig **kein** Protokoll. Unter **Einstellungen > Allgemeine Einstellungen** lässt es sich mit dem Kontrollfeld **„Protokolldatei totalScanX.log schreiben“** einschalten. **Standard ist aus.** Das Ein- und Ausschalten gilt sofort, ohne Neustart; beim Einschalten werden Systemangaben und Scanner sofort ins Protokoll geschrieben. Das Protokoll hilft bei der Fehlersuche und kann im Problemfall an den Support geschickt werden.

**Startparameter `-log`:** Wird totalScanX mit dem Parameter `-log` gestartet, schreibt es in dieser Sitzung immer ein Protokoll, auch wenn es in den Einstellungen ausgeschaltet ist. Die Einstellung selbst bleibt dabei unverändert; beim nächsten normalen Start gilt wieder sie. Das ist für die Fehlersuche auf einem anderen Rechner gedacht: Sie müssen dort nichts umstellen. So geht es:

1. Drücken Sie **Windows+R**, um das Ausführen-Fenster zu öffnen.
2. Geben Sie den vollständigen Pfad zum Programm in Anführungszeichen ein, dahinter ein Leerzeichen und `-log`, zum Beispiel: `"C:\Programme\totalScanX\totalScanX.exe" -log`
3. Drücken Sie die **Eingabetaste**.

Alternativ legen Sie eine Verknüpfung an und hängen im Feld **Ziel** ` -log` an. Im Protokoll steht dann beim Start „(Startparameter -log)“. Statt `-log` werden auch `/log` und `--log` erkannt.

Ist es eingeschaltet, schreibt das Programm in **`totalScanX.log`** im Programmordner (falls dort nicht schreibbar: `%APPDATA%\totalScanX`). Die Datei wird fortlaufend ergänzt und enthält

- beim Start: Programmversion, Betriebssystem mit Version und 32/64 Bit, alle gefundenen Scanner mit Schnittstelle (WIA oder TWAIN) und den gewählten Scanner,
- beim Start außerdem, was jeder Scanner laut Treiber kann: Vorlagenglas, Einzug, beidseitiges Scannen, Auflösungen, Farbarten und Bildformate. Dafür wird nichts gescannt; die Angaben helfen bei der Fehlersuche und bei der Unterstützung weiterer Scanner,
- jeden Scan (Schnittstelle, Auflösung, Dauer, Größe), Erfassungen, Öffnen und Speichern von Dateien, Updates,
- alle **Fehler** mit Fehlertext und technischer Fehlerverfolgung, auch unerwartete,
- Ihre **Bedienung**: jede Tastenkombination und Sondertaste (zum Beispiel „Taste F4“, „Taste Strg+S“, „Taste Tab“) mit dem Element, in dem der Fokus stand, jeden Menübefehl, jede gedrückte Schaltfläche, jedes ein- oder ausgeschaltete Kontrollkästchen und jede Auswahl in Listen,
- jedes **Dialog- und Meldungsfenster** mit Titel, Meldungstext und Ihrer Antwort (OK, Ja, Nein, Abbrechen),
- alle **Ansagen**, die das Programm gemacht hat (Statusleiste und NVDA),
- jeden **Profilwechsel** und jede **geänderte Einstellung** (alter und neuer Wert),
- die **einzelnen Schritte einer Erfassung**: die Einstellungen des verwendeten Profils, Scan, Ausrichtung (Drehung), Entsprenkeln, die gewählte Erkennungssprache samt Konfidenzwerten, Dauer und Zahl der erkannten Wörter je Seite,
- beim Start außerdem die Größe der Sprachdaten (Deutsch, Englisch).

Der **Inhalt Ihrer Dokumente und getippte Buchstaben werden nicht protokolliert**; Zeichen, die Sie nur eintippen, und der erkannte Text bleiben außen vor. Aufgezeichnet werden nur Sondertasten und Tastenkombinationen sowie Wortanzahlen.

Bitte schicken Sie bei Problemen diese Datei mit.

## 15. Scanner: WIA und TWAIN

- **WIA** wird von fast allen Heimscannern unterstützt und ist die Standardschnittstelle von totalScanX.
- Manche Scanner mit neuerem WIA-Treiber geben das Bild nur über die Scanschnittstelle heraus, die auch die Windows-eigenen Scanprogramme verwenden. totalScanX erkennt das selbst und scannt dann auf diesem Weg; Sie müssen nichts einstellen. Der erste Scan nach dem Einschalten kann dabei etwas länger dauern, weil der Scanner seine Lampe aufwärmt.
- **TWAIN** wird ebenfalls unterstützt (Scan ohne Treiberoberfläche). Wichtig: Die Bitbreite des TWAIN-Treibers muss zu der des Programms passen. Viele Scannertreiber bringen nur ein 32-Bit-TWAIN-Modul mit; das sieht eine 64-Bit-Fassung von totalScanX nicht. Dann hilft die Nutzung über WIA oder eine 32-Bit-Fassung des Programms. Der TWAIN-Scan selbst ist bisher **nicht praktisch getestet**, weil auf dem Entwicklungsrechner keine TWAIN-Quelle sichtbar war.
- Beide Schnittstellen erscheinen in der Geräteauswahl; dasselbe Gerät kann doppelt auftauchen.

## 16. Tastenübersicht

- F1, Handbuch
- F2, Mit KI bearbeiten (Zusammenfassen, Fragen, Übersetzen …)
- F3, Brief auf einen Blick (Absender, Datum, Art, Betrag, Frist)
- F4, Seite erfassen
- Leertaste (nur im Nur-Lese-Modus), Seite erfassen
- Esc (während einer Erfassung), Erfassung abbrechen
- Strg+Umschalt+F4, Erfassen und aktuelle Seite ersetzen
- Strg+Umschalt+F3, Schnellvorschau (nur den oberen Teil scannen)
- Strg+Umschalt+Y, Spalten erkennen ein/aus
- Alt+S, A, Ausrichtung der eingelegten Seite prüfen
- F7, In allen Dokumenten suchen
- F8, Als Hörfassung speichern (MP3 oder WAV)
- F9, Lesezeichen verwalten
- Strg+F9, Lesezeichen einfügen
- Strg+N, Neues Dokument
- Strg+O, Öffnen
- Strg+S, Speichern
- Strg+Umschalt+S, Seiten speichern
- Strg+P, Drucken
- Strg+F4, Dokument schließen
- Strg+F6, Dokument umschalten
- Alt+F4, Beenden
- Strg+Z, Rückgängig
- Strg+X, Ausschneiden
- Strg+C, Kopieren
- Strg+V, Einfügen
- Strg+A, Alles markieren
- Strg+F, Suchen
- Strg+Umschalt+F, Weitersuchen
- Strg+H, Ersetzen
- Strg+E, Bearbeitungsmodus ein/aus
- Strg+Eingabe, Seitenumbruch einfügen
- Strg+Umschalt+Entf, Seitenumbruch löschen
- Strg+Entf, Seite löschen
- Strg+Bild ab, nächste Seite
- Strg+Bild auf, vorherige Seite
- Strg+Umschalt+Bild ab, letzte Seite
- Strg+Umschalt+Bild auf, erste Seite
- Strg+G, Gehe zu
- Strg+Umschalt+V, Text- oder Originalansicht
- Strg+Umschalt+R, Bild nach rechts drehen
- Strg+Umschalt+Q, Bild nach links drehen
- Strg+Plus, Zoom größer
- Strg+Minus, Zoom kleiner
- Strg+Umschalt+W, auf Seitenbreite zoomen

## 17. Was totalScanX (noch) nicht kann

Nicht enthalten: Sprachausgabe und „Alles lesen“ (dafür ist der Screenreader da), Hervorhebungen, Kommentare, Wörterbuch, Rechtschreibprüfung, Thesaurus, Punktschrift-Export, Kamera-Unterstützung, Anzeigeeinstellungen für Sehbehinderte (Farben, Schrift), Wahl einer Erkennungsstrategie (schnell/genau), Erfassen aus Word, Erfassen im Hintergrund per Tastenkombination. Das Erfassen und Erkennen läuft mit Fortschrittsdialog und nicht im Hintergrund; währenddessen kann nicht im Dokument gearbeitet werden. Duplex-Scan und Papiereinzug werden nicht gesondert angesteuert.

## 18. Fehlersuche

- „Kein Scanner gefunden“: Kabel, Einschalten, Transportsicherung entriegeln, Treiber, andere Scanprogramme schließen; dann „Erneut suchen“.
- „Der Scannerkopf ist gesperrt“: Mechanische Transportsicherung am Scanner entriegeln, Scanner aus- und einschalten.
- Scan schlägt gelegentlich fehl: Das Programm versucht es einmal erneut. Scanner kurz warten lassen; im Protokoll steht der Fehlertext.
- Text ist Buchstabensalat: Meist falsch ausgerichtete Vorlage; das Programm dreht automatisch. Sonst Auflösung erhöhen oder „Ausrichtung der eingelegten Seite prüfen“ nutzen. Bei aufgeschlagenen Heften oder Büchern (zwei Seiten nebeneinander) „Doppelseite in zwei Seiten teilen“ einschalten oder mit dem Profil „Erfassen mit KI“ erfassen.
- Fehlende Sprachdaten: Werden vor dem Scan zum Download angeboten (Internet nötig).
- KI antwortet nicht / nicht eingerichtet: Einstellungen > Lokale KI installieren wählen.
- Ein Tastendruck am Scanner startet zusätzlich ein anderes Scanprogramm: Windows meldet jeden Tastendruck an alle Programme, die sich dafür eingetragen haben; totalScanX kann das nicht verhindern. Abhilfe: Unter Windows in den Eigenschaften des Scanners (Systemsteuerung > Geräte und Drucker > Rechtsklick auf den Scanner > Scannereigenschaften) auf der Registerkarte „Ereignisse“ für die Taste „Kein Programm starten“ wählen, oder das andere Programm schließen bzw. dort die Scannertasten abschalten.
- Meldung „Die Erkennung ist unsicher“: Seite gerade und vollständig auflegen, Deckel schließen, bei kleiner Schrift die Auflösung im Profil erhöhen; oder die Seite mit der lokalen KI neu lesen lassen.
- Hörfassung: keine oder nur englische Stimme: In den Windows-Einstellungen unter Zeit und Sprache > Sprachausgabe eine deutsche Stimme hinzufügen.
- „In allen Dokumenten suchen“ findet nichts: Durchsucht wird nur der Ordner für Ihre Dokumente (Einstellungen > Allgemeine Einstellungen) mit Unterordnern, und nur .tsx- und .txt-Dateien.
- Etwas anderes: Datei `totalScanX.log` ansehen und weitergeben.

---

## Änderungsverlauf

- 2026.11.24: totalScanX wird jetzt auf GitHub unter nvda-nachhaltig/totalScanX veröffentlicht. „Nach Updates suchen“ lädt die neue Programmdatei von dort, ersetzt die alte nach dem Beenden und startet die neue Version. Ältere Versionen suchen noch an der alten Stelle; sie müssen einmal von Hand durch diese Version ersetzt werden.
- 2026.11.23: Beim Start konnten die Scannertasten ausfallen, weil zwei Programmteile gleichzeitig auf den Scanner zugriffen („Das WIA-Gerät ist ausgelastet“). Jetzt greift immer nur ein Teil zu; ist der Scanner gerade durch ein anderes Programm belegt, versucht totalScanX es nach kurzer Pause erneut.
- 2026.11.23: Beim Schließen konnte die Meldung „Failed to remove temporary directory“ erscheinen. Programme, die totalScanX im Hintergrund startet (zum Beispiel die lokale KI), werden jetzt so gestartet und beendet, dass sie den temporären Ordner des Programms nicht mehr blockieren.
- 2026.11.23: Im Menü Navigation sind die vier Befehle zum Blättern im Untermenü „Seite wechseln“ zusammengefasst: Erste Seite, Letzte Seite, Vor und Zurück. Die Tasten bleiben gleich.
- 2026.11.23: Das Handbuch kommt ohne Tabellen aus. Tastenkürzel, Profile und Lösungen stehen jetzt in Listen, zum Beispiel „Strg+F9, Lesezeichen einfügen“; das lässt sich mit jedem Screenreader und auf der Braillezeile gut lesen. Die Tastenübersicht nennt jede Taste in einer eigenen Zeile.
- 2026.11.22: Auch bei offenem Scannerdeckel ohne Vorlage meldet F4 jetzt „Leere Seite.“, auch wenn sich Licht auf dem Glas spiegelt. Eine Vorlage bei offenem Deckel, etwa eine kleine Karte, wird weiterhin erkannt.
- 2026.11.22: Leere Seiten werden zuverlässiger erkannt; Staub, Schatten am Rand oder ein leicht grauer Deckel zählen nicht mehr als Inhalt. Dadurch meldet F4 bei leerem Scanner mit allen Profilen sofort „Leere Seite.“, und auch die Prüfung der Ausrichtung erkennt den leeren Scanner sicherer. Wird auf einer nicht leeren Seite kein Text erkannt, sagt das Programm „Kein Text erkannt.“
- 2026.11.22: Eine leere Seite wird beim Erfassen (F4, mit Texterkennung oder KI) gleich nach dem Scan als „Leere Seite.“ gemeldet, ohne vorher Erkennung oder KI zu starten.
- 2026.11.22: Strg+Entf in einem leeren Dokument sagt jetzt sofort „Keine Seite zum Löschen vorhanden.“ statt erst die Rückfrage zum Löschen zu zeigen.
- 2026.11.22: „Ausrichtung der eingelegten Seite prüfen“ läuft jetzt ohne Dialog im Hintergrund wie das Erfassen: Ansage „Ausrichtung wird geprüft.“ zu Beginn, Arbeitston und Statusleiste währenddessen, Esc bricht ab, am Ende wird das Ergebnis angesagt.
- 2026.11.22: „Ausrichtung der eingelegten Seite prüfen“ meldet bei leerem Scanner jetzt „Auf dem Scanner wurde keine Seite mit Text gefunden.“ statt „richtig ausgerichtet“. Auch die Ansage, wie die Seite im Scanner lag, entfällt, wenn auf der Seite kein Text gefunden wird.
- 2026.11.22: Das Protokoll hält beim Start fest, welche Scanquellen jeder Scanner anbietet (Vorlagenglas, Einzug, beidseitig) und welche Auflösungen, Farbarten und Formate er kann. Gescannt wird dafür nichts. Das bereitet die Unterstützung von Scannern und Multifunktionsgeräten mit Einzug vor.
- 2026.11.22: Scheitert ein Scan über WIA, schreibt das Protokoll jetzt genauere Angaben zum Scannertreiber und zum Ausweichweg über die Windows-Scanschnittstelle. Das hilft bei der Fehlersuche mit Scannern, die auf dem Entwicklungsrechner nicht vorhanden sind. Starten Sie totalScanX dafür mit dem Parameter `-log` (Abschnitt 14).
- 2026.11.21: Das Handbuch beginnt jetzt mit einem Inhaltsverzeichnis. Ein Link darin springt zum Kapitel; im Handbuch (F1) steht der Fokus danach auf der Überschrift, und der Screenreader liest dort weiter. Die Links funktionieren auch auf GitHub.
- 2026.11.21: Das Handbuch heißt jetzt readme.md. Es ist weiterhin in der Programmdatei enthalten und wird mit F1 angezeigt.
- 2026.11.21: Im Menü Einstellungen entfällt der Eintrag „Beim Start nach Updates suchen“; die Einstellung finden Sie weiterhin unter Einstellungen > Allgemeine Einstellungen auf der Registerkarte Allgemein.
- 2026.11.21: Das Kontrollfeld in den Allgemeinen Einstellungen heißt jetzt nur noch „Protokolldatei totalScanX.log schreiben“, ohne den Zusatz zum Standardwert.
