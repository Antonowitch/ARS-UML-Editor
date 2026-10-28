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
| Windows | `ARS-UML-Editor V3.2 starten.bat` doppelklicken |
| macOS | `ARS-UML-Editor V3.2 starten.command` doppelklicken — beim ersten Mal einmalig `chmod +x` nötig, siehe LIESMICH |
| überall | `java -jar ARS-UML-Editor-V3.2.jar` |

**Hinweis für macOS:** Das Aussehen der Fenster kommt seit V3.2 von der Bibliothek
[FlatLaf](https://www.formdev.com/flatlaf/). Deren eigene Titelleiste mit
eingebetteter Menüleiste gibt es auf dem Mac nicht — *„FlatLaf window decorations
and embedded menu bar are not available on macOS"*. Auf dem Mac bleibt deshalb die
gewohnte Titelleiste von macOS, und die Menüleiste steht darunter im Fenster. Alles
andere sieht aus wie auf den Bildern hier und funktioniert genauso.

## Was es kann

### Dunkel oder hell

Seit V3.2 startet der Editor **dunkel**: Fenster, Menüs, Dialoge und
Zeichenfläche. Ein Klick im Menü *Diagramm* macht alles hell, sofort und ohne
Neustart — so wie im letzten Bild dieser Seite. **Exportierte Bilder sind immer
hell**, als PNG wie als SVG: Sie landen auf Arbeitsblättern und im Ausdruck.
Farben mit Bedeutung behalten ihren Ton — Rot für einen Fehler, Blau für die
abgeleiteten Attribute —, nur heller, damit sie auf dunklem Grund lesbar sind.

### Klassendiagramm — und der Umschalter, der den Entwurfsschritt zeigt

Klassen mit Attributen, Methoden, Sichtbarkeiten und Datentypen; Assoziation,
Aggregation, Komposition und Vererbung, dazu Rollennamen, Multiplizitäten,
Leserichtung und Navigierbarkeit. Abstrakte Klassen und Methoden werden kursiv
gesetzt, statische unterstrichen.

![Klassendiagramm in der Analysesicht](bilder/klassendiagramm-analyse.png)

**Strg+D** blendet die Attribute ein, die sich aus den Beziehungen **ergeben** —
blau gezeichnet, rot bei einem Namenskonflikt. Damit wird der Schritt von der
Analyse zum Entwurf und zum Programm sichtbar, statt behauptet zu werden:
dieselbe Beziehung einmal als Linie, einmal als Referenzattribut und im
Java-Export als Feld.

![Dasselbe Diagramm mit den abgeleiteten Beziehungsattributen](bilder/klassendiagramm-entwurf.png)

Die Ableitung folgt den Pfeilen: Ein Pfeil an einem Ende heißt, die Klasse am
anderen Ende bekommt ein Attribut; ein **X** heißt ausdrücklich keines. Der Modus
ist reine Anzeige — das Modell bleibt unverändert.

Und dasselbe Diagramm ein drittes Mal: **ohne Methoden**. Über das
Rechtsklickmenü einer Klasse lassen sich *Attribute anzeigen* und *Methoden
anzeigen* einzeln abhaken; das Fach verschwindet dann ganz. Übrig bleibt die
Struktur — die Klassen, ihre Attribute und die Beziehungen, um die es beim
Besprechen geht. Die Klasse hat ihre Methoden trotzdem, auch im Java-Export.
Wer noch weiter verdichten will, **klappt** eine Klasse ganz **zu**: Dann bleibt
nur der Name stehen.

![Dasselbe Diagramm mit ausgeblendeten Methoden](bilder/klassendiagramm-ohne-methoden.png)

### Beziehungen mit einem Klick

Ein **Rechtsklick auf eine Beziehung** setzt Navigierbarkeit, Aggregation und
Multiplizität für jedes Ende einzeln — ohne Dialog. Wählt man die Aggregation am
anderen Ende, wandert die Raute dorthin, und Rollennamen und Multiplizitäten
bleiben an ihrer Klasse.

![Das Kontextmenü einer Assoziation](bilder/kontextmenue-linie.png)

Der **Linienstil** macht eine Linie **rechtwinklig**: nur noch waagerechte und
senkrechte Stücke, und das bleibt so, wenn man die Kästen verschiebt — der Weg
wird jedes Mal neu gerechnet. **Strg+A** und dann **Strg+E** macht ein ganzes
Diagramm rechtwinklig, **Strg+L** wieder gerade.

### Schnittstellen und generische Klassen

Eine **Schnittstelle** ist eine eigene Art von Kasten: `<<interface>>` steht über
dem Namen, ihre Methoden sind kursiv, und eine Klasse wird mit der **Realisierung**
daran gebunden — gestrichelte Linie, offenes Dreieck. Im Java-Export entsteht daraus
ein echtes `interface` und ein `implements`.

**Generische Klassen** tragen ihre Platzhalter im gestrichelten Kästchen oben
rechts, wie die UML es vorsieht. Datentypen wie `MyLinkedList<T>` lassen sich
überall eintragen, wo ein Typ erwartet wird. Auch der Java-Import erkennt beides
wieder.

Eine **Aufzählung** ist die dritte Art von Kasten: `<<enumeration>>` über dem
Namen, die Konstanten im Fach darunter — und im Export ein echtes `enum`.

Ein Attribut lässt sich als **statisch** und als **final** kennzeichnen. Zusammen
ergeben die beiden die Konstante: `+ MWST : double = 0.19 {readOnly}`,
unterstrichen und mit dem Lesezeichen der UML — im Java-Export
`public static final`.

![Schnittstellen und generische Klassen am Beispiel eines Stapels, im hellen Erscheinungsbild](bilder/schnittstellen-generics.png)

Das Bild zeigt beides zusammen, diesmal im hellen Erscheinungsbild: Die generische
Schnittstelle `Stapel` legt fest, was ein Stapel können muss; `ArrayStapel` erfüllt
sie über ein Array, und `Verlauf` benutzt einen Stapel, ohne zu wissen, welche
Umsetzung dahintersteht. Die Konstante `ANFANGSGROESSE` ist unterstrichen.

### Pakete — Schichten, die man sieht

Ein **Paket** gliedert das Klassendiagramm: der Kasten mit dem Reiter, in dem
Klassen, Schnittstellen, Aufzählungen und weitere Pakete liegen. Hineingezogen
wird mit der Maus oder über das Rechtsklickmenü; das Paket wächst mit seinem
Inhalt und nimmt ihn beim Verschieben mit. Jedes bekommt auf Wunsch eine
**Hintergrundfarbe** — am Beamer ist das der Unterschied zwischen „da sind drei
Kästen" und „da sind drei Schichten". Im dunklen Erscheinungsbild erscheint sie
abgedunkelt im selben Farbton.

![Ein Projekt in den Paketen gui, modell und persistenz](bilder/pakete.png)

Der Ertrag steht an den Linien **zwischen** den Paketen: Die Oberfläche kennt das
Modell und den Speicher — umgekehrt weiß das Modell von beiden nichts. Dafür gibt
es die **Abhängigkeit**, die gestrichelte Linie mit offener Spitze: „A benutzt B".
Sie ist die richtige Linie, wenn eine Klasse eine andere *braucht*, aber nicht
*hat* — als Parameter, als Rückgabewert, oder weil sie sie in einer Methode
erzeugt. Ein Feld wäre dann falsch und eine Assoziation damit auch. Als einzige
Beziehung darf sie auch von Paket zu Paket gehen. Und das `~` vor `DateiSpeicher`
heißt, dass die Klasse nur in ihrem eigenen Paket sichtbar ist: Das Hauptfenster
hängt an der **Schnittstelle** `Speicher`, nicht an der Umsetzung. Der Java-Export
hält sich daran, und der Übersetzer weist einen Zugriff von außen zurück.

**Zuklappen** macht aus demselben Diagramm eine Übersicht. Rechtsklick, und von
einem Paket bleiben Reiter und Name; die Beziehungen nach außen enden am
Paketkasten, mehrere zum selben Ziel werden zu einer zusammengefasst. Übrig bleibt
genau die Frage, um die es dann geht: Welches Paket hängt von welchem ab?

Im **Java-Export** wird aus jedem Paket ein Unterordner mit eigener
`package`-Zeile; benutzt eine Klasse eine aus einem anderen Paket, schreibt der
Editor die `import`-Zeile dazu. Der erzeugte Quelltext lässt sich übersetzen.

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

![Use-Case-Diagramm einer Wettbewerbsverwaltung](bilder/use-case-diagramm.png)

### Dazu

**Java-Quelltext in beide Richtungen.** Aus dem Klassendiagramm entstehen
`.java`-Dateien mit Attributen, Konstruktor und auf Wunsch Gettern und Settern.
Umgekehrt liest der Editor vorhandene `.java`-Dateien ein und zeichnet daraus ein
Klassendiagramm — mit Vererbung und Assoziationen.

**Export als PNG und als SVG.** Das Vektorbild bleibt beim Vergrößern scharf —
für Arbeitsblätter, Beamer und Ausdruck; LibreOffice und Word fügen es ein wie
jedes andere Bild. Ist etwas **ausgewählt**, wird nur dieser Ausschnitt
exportiert, eng zugeschnitten. Exportiert wird immer hell.

**Ordnung im Bild.** Elemente lassen sich aneinander **ausrichten** und mittig
setzen, ein **Raster** ein- und ausblenden und getrennt davon **einrasten**.
Beziehungslinien knicken um Kästen herum oder laufen rechtwinklig, Rollennamen und
Multiplizitäten lassen sich verschieben, und eine **freie Linie** dient als reine
Anmerkung — etwa um in einem Sequenzdiagramm zu zeigen, welche Daten zwischen zwei
Aufrufen übertragen werden.

**Vierzehn Beispielprojekte** liegen bei, von der einfachen Bank bis zu einem
Chorwettbewerb, einer Client-Server-Kommunikation, einer in Pakete gegliederten
Schulverwaltung und einem Webshop mit Aufzählungen und Abhängigkeiten. Jedes ist in
der beiliegenden LIESMICH einzeln beschrieben — mit dem, was sich daran zeigen
lässt, und mit Fragen für den Unterricht.

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

### Verwendete Bibliothek

Seit V3.2 enthält das Programm **[FlatLaf](https://github.com/JFormDesigner/FlatLaf)**
3.7.2 von FormDev Software — für das Aussehen der Fenster, hell und dunkel. FlatLaf
steht unter der **Apache License 2.0**; deren Text liegt dem Paket als
`LIZENZ-FlatLaf.txt` bei und steckt zusätzlich in der JAR. Die Einschränkungen der
Nutzungserlaubnis oben gelten nur für den ARS-UML-Editor selbst, nicht für FlatLaf.
