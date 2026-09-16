# ARS-UML-Editor

Ein Editor für **UML-Diagramme**: Klassendiagramm, Objektdiagramm,
Sequenzdiagramm und Use-Case-Diagramm — in einem Projekt, in einer Datei.

Entstanden für die Informatik im Beruflichen Gymnasium an der ARS. Läuft unter
Windows, macOS und Linux; gebraucht wird nur **Java 17 oder neuer**. Keine
Installation, kein Setup, keine Internetverbindung — der Ordner läuft auch von
einem Stick.

## Herunterladen

Das fertige Paket liegt unter **[Releases](../../releases/latest)** —
eine ZIP-Datei, auspacken, starten.

| | |
|---|---|
| Windows | `ARS-UML-Editor V2.0 starten.bat` doppelklicken |
| macOS | `ARS-UML-Editor V2.0 starten.command` doppelklicken — beim ersten Mal einmalig `chmod +x` nötig, siehe LIESMICH |
| überall | `java -jar ARS-UML-Editor-V2.0.jar` |

## Was es kann

### Klassendiagramm — und der Umschalter, der den Entwurfsschritt zeigt

Klassen mit Attributen, Methoden, Sichtbarkeiten und Datentypen; Assoziation,
Aggregation, Komposition und Vererbung, dazu Rollennamen, Multiplizitäten,
Leserichtung und Navigierbarkeit. Abstrakte Klassen und Methoden werden kursiv
gesetzt, statische unterstrichen.

![Klassendiagramm in der Analysesicht](bilder/klassendiagramm-analyse.png)

**Strg+D** blendet die Attribute ein, die sich aus den Beziehungen **ergeben** —
blau gezeichnet, rot bei einem Namenskonflikt. Damit wird der Schritt von der
Analyse zum Entwurf sichtbar, statt behauptet zu werden: Dieselben Beziehungen,
einmal als Linie und einmal als Referenzattribut.

![Dasselbe Diagramm mit den abgeleiteten Beziehungsattributen](bilder/klassendiagramm-entwurf.png)

Die Ableitung folgt den Pfeilen: Ein Pfeil an einem Ende heißt, die Klasse am
anderen Ende bekommt ein Attribut; ein **X** heißt ausdrücklich keines. Der Modus
ist reine Anzeige — das Modell bleibt unverändert.

### Objektdiagramm

Zu jedem Klassendiagramm beliebig viele Objektdiagramme, jedes in einem eigenen
Reiter. Der Editor prüft dabei mit: Ein Objekt einer **abstrakten** Klasse gibt es
nicht, eine Verknüpfung ohne Beziehung im Klassendiagramm auch nicht, und eine
überschrittene Multiplizität wird gemeldet.

![Objektdiagramm zum Sportfest](bilder/objektdiagramm.png)

### Sequenzdiagramm

Lebenslinien mit Aktivierungsbalken, synchrone und asynchrone Nachrichten,
Antworten, Selbstaufrufe, Erzeugung und Zerstörung, dazu Fragmente
(`loop`, `alt`, `opt`, …) und Notizen. Die **Reihenfolge** der Nachrichten ist
das Modell: Sie werden mit Alt+Pfeil umsortiert, die Höhen rechnet das Programm.
Mehrere Abläufe dürfen nebeneinanderstehen — etwa Server- und Clientseite eines
Netzprogramms.

![Sequenzdiagramm einer Client-Server-Kommunikation](bilder/sequenzdiagramm.png)

### Use-Case-Diagramm

Akteure, Anwendungsfälle, `include` und `extend` mit Bedingungszettel,
Erweiterungsstellen und Generalisierung. Der **Systemrahmen** wird nicht
gezeichnet, sondern **abgeleitet**: Er umschließt immer alle Anwendungsfälle und
lässt die Akteure außen vor — genau das, was er aussagen soll.

![Use-Case-Diagramm einer Flugticketverwaltung](bilder/use-case-diagramm.png)

### Dazu

**Java-Quelltext in beide Richtungen.** Aus dem Klassendiagramm entstehen
`.java`-Dateien mit Attributen, Konstruktor und auf Wunsch Gettern und Settern.
Umgekehrt liest der Editor vorhandene `.java`-Dateien ein und zeichnet daraus ein
Klassendiagramm — mit Vererbung und Assoziationen.

**Export als PNG und als SVG.** Das Vektorbild bleibt beim Vergrößern scharf —
für Arbeitsblätter, Beamer und Ausdruck; LibreOffice und Word fügen es ein wie
jedes andere Bild. Ist etwas **ausgewählt**, wird nur dieser Ausschnitt
exportiert, eng zugeschnitten.

**Elf Beispielprojekte** liegen bei, von der einfachen Bank bis zu einem
Chorwettbewerb und einer Client-Server-Kommunikation.

**Eine ausführliche Anleitung steckt im Programm** — Taste **F1**. Sie erklärt
jedes Werkzeug, die vier Diagrammarten und die Regeln, nach denen der Editor
mitprüft.

## Für Lehrkräfte

Der Editor kennt eine **Klassenbibliothek**: fertig modellierte Klassen, die sich
mit zwei Klicks ins Diagramm holen lassen. In dieser Fassung liegt davon eine
**kleine Auswahl** bei — elf Klassen, je eine pro Sachgebiet, als Anschauung
dafür, wie eine sauber modellierte Klasse aussieht.

Die **vollständige Bibliothek mit 184 Klassen** in dreizehn Kategorien gibt es auf
Anfrage. Schreiben Sie mich an und nennen Sie Ihre Schule.

**Der Grund für die Trennung:** Attribute und Methoden aus einem Pflichtenheft
abzuleiten ist genau der Schritt, den die Schülerinnen und Schüler üben sollen.
Läge für jede Aufgabe die fertige Klasse bereit, übt ihn niemand mehr. Alles
andere kann diese Fassung uneingeschränkt — auch eigene Klassen in die Bibliothek
aufnehmen und sie als `.ARScls`-Datei weitergeben.

## Warum hier nur das Programm liegt

Der Quelltext ist nicht Teil dieser Veröffentlichung; weitergegeben werden soll
das Paket unverändert. Lehrkräfte, die für ihren eigenen Unterricht hineinsehen
möchten, dürfen mich gerne fragen. Einzelheiten in der
[Nutzungserlaubnis](LIZENZ.md).

## Lizenz

Kostenlos nutzbar und weitergebbar für Unterricht, Ausbildung und
Selbststudium; keine kommerzielle Nutzung. Siehe **[LIZENZ.md](LIZENZ.md)**.

Ohne Gewährleistung.
