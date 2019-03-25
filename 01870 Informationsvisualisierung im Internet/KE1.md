# 1 Motivation und Einführung

**Ziel der Informationsvisualisierung:**

> Repräsentation abstrakter Daten, so dass strukturelle Zusammenhänge und relevante Eigenschaften intuitiv erfasst werden können. Kognitive Prozesse sollen so effektiver unterstützt werden.

## 1.1 Ursprünge und Entwicklung der IV

- erste Arbeiten bereits 1786
- mit Aufkommen leistungsfähiger 3D-Hardware erste Visualisierungsansätze für abstrakte Daten
- Ergänzung um Echtzeitanimation und -interaktion

Begriff der IVIS ist nicht auf digitale Medien beschränkt, heute jedoch überwiegend so verwendet.

## 1.2 Informationsdialoge - Mensch-Maschine-Interaktion mit Inforationssystemen

Informationsmengen am Beispiel eines Suchvorgangs im Internet:

1. Die **Inhaltsmenge** ist die Menge der **Informationsobjekte** (Daten, Dokumente, ...) die das Informationssystem anbieten kann
2. Die **Interessenmenge** ist diejenige Menge der Informationsobjekte, die geeignet sind um das **Informationsbedürfnis** (um eine Aufgabe zu erfüllen oder ein Problem zu lösen) des Anwenders zu erfüllen
3. Die **Relevanzmenge R** ist der Schnitt aus Inhaltsmenge (vom System) und Interessenmenge (vom Nutzer). (Alle anderen Elemente sind generell nicht von Interesse.)
4. Durch verschiedene Suchanfragen (explorativer Charakter) entstehen mehrere **Ergebnismengen**, die einen Schnitt zwischen Inhaltsmenge und Relevanzmenge bilden. (Das heißt, dass System zeigt evtl. mehr Ergebnisse an als interssant sind)
5. Ergebnismengen überlappen sich in der Praxis nicht vollständig mit Relevanzmenge, daher wird der Schnitt zwischen allen Ergebnismengen häufig **Kernmenge** genannt

> Ziel ist es die Kernmenge auf die komplette Relevanzmenge auszuweiten.

## 1.3 Modelle zur Informationsvisualisierung

Informationsvisualisierung ist im Wesentlichen ein Abbildungsprozess.

Das **Referenzmodell der Informationsvisualisierung** (nach Card et. al., 1999) ist eine konzeptionelle Beschreibung dieses Transformationsprozesses von Rohdaten, über strukturierte Daten, über visuelle Strukturen bis zu Sichten (Abbildungen).

Über die Sichten kann der Anwender interagieren indem er an den verschiedenen Schritten des Prozesses Parameter ändert.

1. Die **Rohdaten** liegen als Datensatz vor
2. Erster Schritt: *Datentransformation* um **strukturierte Daten** zu erhalten (nicht immer notwendig, bspw. wenn bereits strukturierte Messdaten vorliegen)
3. Zweiter Schritt: durch *visuelles Mapping* wird das Datenmodell und Datenschema mit dem Visualisierungsmodell und Visualisierunsschema in Verbindung gebracht. Es entstehen **visuelle Strukturen**.
4. Dritter Schritt: die entstandenen visuellen Strukturen werden durch eine *Sichtentransformation* in die eigentlichen **Sichten** transformiert

Das **Datenstatusmodell** (nach Chi und Riedel, 1998) ist eine Erweiterung des Referenzmodells mit klarer definierten Transformationsschritten.

## 1.4 Daten- und Datentransformation

Die **Datentransformation** ist der erste Schritt zur IVIS, der jedoch nicht immer notwendig ist (bspw. wenn die Rohdaten bereits in strukturierter Form vorliegen).

Transformation kann auf viele Arten geschehen: Filtern, Gruppieren, Hinzufügen von Meta-Daten, Untermengen bilden, ...

## 1.5 Visuelle Abbildung

Die **visuelle Abbildung (Mapping)** ist der entscheidende Schritt bei der Informationsvisualisierung. Hier werden grafische Symbole und Eigenschaften hinzugefügt.

> **Visuelle Abbildungen** bilden Daten und deren Strukturen auf eine visuelle Repräsentation ab. Dazu stehen verschiedene visuelle Attibute zur Verfügung.

Eine gute visuelle Abbildung ist **expressiv** (ausdrucksstark) und **effektiv**. Sie bedient sowohl bewusste als auch unbewusste kognitive Vorgänge. Die Abbildungen sollten möglichst so gewählt werden, dass Verständnis und Wahrnehmung weitestegehend unbewusst abgewickelt werden kann.

**Expressiv:** Alle relevanten Daten - und nur diese - werden dargestellt.

**Effektiv:** Visuelle Abbildung nutzt optimal die Möglichkeiten des Ausgabemediums und die visuellen Fähigkeiten des Menschen.

### 1.5.1 Strukturabbildungen

> Strukturabbildungen als erste wesentliche Komponente von visuellen Abbildungen.

visuelle Darstellungsachsen:

1. unstrukturierte Achsen
2. nominale Achsen (Region ist in Unterregionen unterteilt)
3. ordinale Achsen (auf den Unterregionen ist eine Ordnung definiert)
4. quantitative Achsen (einer Region ist eine Metrik zugeordnet)

Erhöhung der Informationsmenge durch

1. Komposition
2. Anordnung
3. Faltungen
4. Rekursion
5. Überladen

### 1.5.2 Attribut-Abbildungen

> Attributabbildungen als zweite wesentliche Komponente von visuellen Abbildungen.

- Verwendung von visuellen Zeichen, Symbolen und Markierungen
- Attribute sind bspw. Farbe, Helligkeit, Sättigung, Form, Textur, ...

### 1.5.3 Visuelle Skalierbarkeit

Messbarkeit von visueller Skalierbarkeit als mathematische Funktion:

    responses = F(factors, data)

Erkentnisse sind jedoch schwer quantifizierbar, daher Ersatz durch einfache Skalierbarkeitsmetriken:

1. Datenbank-Metriken
2. Informationsvisualisierungscharakteristika

Relevante Faktoren die die Wahnehmung beeinflussen:

1. menschliche Wahrnehmung
2. Bildschirmauflösung
3. visuelle Metaphern
4. Interaktivität
5. Datenstrukturen und Verarbeitungsalgorithmen
6. Recheninfrastuktur

## 1.6 Visuelle Wahnehmung und Kognition

Erweiterung des Referenzmodells der Visualisierung durch **Wahnehmungs- und Kognitionskomponente** sowie **abstrakte Wissenskomponente**.

### 1.6.1 Visuelle Wahnehmung von Bildschirmen und deren Auflösungen

Zwei Basiskonzepte zur Relevanz:

1. visueller Winkel und Abstand zum Bildschirm
2. Sehschärfe

Gegenstück zu Bildschirmpixel: **vereinfachtes Modell der Gehirnpixel**. Bei circa 6 Grad Sichtwinkel wird die **Sehgrube** (bereich höchster Sehschärfe) genutzt. Kleine und hochauflösende Bildschirme haben die größte visuelle Effizienz.

### 1.6.2 Ein Modell für die visuelle Informationsverarbeitung

**1. Phase** Paralleles Extrahieren von einfachen Eingenschaften der visuellen Szene: geschieht unbewusst, parallel und sehr schnell. Die Informationen haben transiente Natur.

**2. Phase** Musterwahrnehmung: das visuelle Feld wird in Regionen und einfache Muster zerlegt. Ist langsam und seriell und bezieht Langzeitgedächtnis mit ein.

**3. Phase** Sequentielle und zielgerichtete Verarbeitung

### 1.6.3 Elementare visuelle Wahrnehmung

Vier Gruppen von Wahrnehmungseigenschaften:

1. assoziative Wahrnehmung (Wie stark wirkt sich die vis. Variable auf di anderen Dimenstionen aus?)
2. selektive Wahrnehmung (Wie gut grenzt eine vis. Variable ein Element von anderen ab?)
3. Wahrnehmung der Anordnung (Wie gut ist die Rangordnung der Elemente wahrnehmbar?)
4. quantitative Wahrnehmung (Wie gut sind Elemente anhand der Menge der Unterschiede unterscheidbar?)

- Erste Phase der Informationsverarbeitung wird auch **präattentiv** genannt und geschieht bevor Aufmerksamkeit des Benutzers aktiv auf Details gerichtet wird.
- ist unabhängig vom Stresslevel der Person
- visuelle Attribute die präattentiv sind: Form, Farbe, Bewegung räumliche Position in jeweils verschiedenen Ausprägungen

### 1.6.4 Zeitschranken der Wahrnehmung

> **Änderungsblindheit** ist der Effekt, dass große Änderungen an einer IVIS werden nicht wahrgenommen, wenn zeitglich irrelevante Änderungen auftreten, es eine Unterbrechung der Wahrnehmung gab, oder Ähnliches.

Drei zeitabhängige Stufen der Wahrnehmung:

**1. Psychologisches Moment:** (0,1 Sekunden), Reize in dieser Zeitspanne verschmelzen in der Wahnehmung.

**2. Unvorbereitete Rückmeldung:** (1 Sekunde), Maßstab für reibungslose Interaktion mit dem Anwender, wenn dieser nicht darauf vorbereitet ist.

**3. Aufgabeneinheit:** (10 Sekunden), Durchführung von bewusst wahrgenommenen Routineaktionen.

### 1.6.5 Kongnitionsunterstützung und kognitive Verstärkung

**Kognitionsunterstützung:** Unterstützung menschlicher "Denkleistung"

**externe Wahrnehmung:** TODO

**kognitive Kosten:** TODO

## 1.7 Begriff der Informationsvisualisierung

> **Visualisierung** ist der Gebrauch von computergestützten, interaktiven visueller Darstellungen von Daten, um deren Verständnis zu erleichtern.

Im Kurs:

> **Informationsvisualisierung** ist der Gebrauch von computergestützten, interaktiven visueller Darstellungen von abstrakten Daten, um deren Zugruff, Wahrnehmung, Interpretation und Verständnis zu erleichtern.

- Unterschied: abstrakte Daten haben naturgemäß keine physische Erscheinungsform.

> **Wissenschaftliche Visualisierung** bezieht sich auf die Darstellung von physischen Daten, zum Beispiel in Form von Messwerten aus der realen Welt.

## 1.8 Interaktionen und Interaktionstechniken

- Interaktion ist wichtige Ergänzung in der Informationsvisualisierung

### 1.8.1 Interaktionen

Fenster innerhalb einer Benutzeroberfläche besteht aus Sicht (*view*) und Sammlung von Elementen (*items*). Bestandteile sind durch grundlegende Interaktion miteinander verbunden:

1. **Selektion von Objekten**
2. **Navigieren von Sichten**

### 1.8.2 Selektionstechniken

- Hervorheben (Selektionsrahmen)
- Filterung
- Projektion
- Dynamic Queries
- Linsentechnik

### 1.8.3 Navigationstechniken

- Scrolling / Panning
- geometrisches Zoomen
- semantisches Zoomen
- Camera Movement / Rotating

### 1.8.4 Übersicht und Detail

- oft eng verwandt mit der Zooming-Technik
- Übersicht-und-Detail-Techniken haben immer den Zielkonflikt der Aufteilung der Arbeitsfläche zwischen Übersicht und Detail

### 1.8.5 Fokussierungstechnik

Unterschied zu Navigationstechniken: Überblick über alle Objekte in der Regel noch möglich. Der gesamte Informationsraum wird angezeigt. Drei Prämissen für die Entwicklung von Fokussierungstechniken:

1. Beide Bereiche (Übersicht und Detail) werden dargestellt
2. Beide Bereiche werden auf derselben dynamischen Sicht dargestellt
3. Informationen in der Übersicht können von der Detailansicht unterscheiden

Periphere Informationen im Kontext reduzieren durch:

- Filterung oder Projektion
- Selection aggregation (ähnliche Objekte zusammenfassen)
- Micro-macro-Readings
- Highlighting (z.B. Unschärfefokussierung)
- Distorsionstechniken (geometische Verzerrung)
- Fisheye-View

### 1.8.6 Interaktionstechniken in multiplen Sichten

2x3-Taxonomie für multiple Sichten:

- Beschreibung der ersten Dimenstion durch Kombination der Grundoperationen von Selektion von Objekten und Navigieren von Sichten
- zweite Dimension: haben die Sichten die gleichen oder unterschiedliche Daten?

### 1.8.7 Interaktionstechniken innerhalb der Informationsvisualisierung

**Interaktionstechniken für Datentransformationen:**

1. Direct Walk
2. Details-on-Demand
3. Attribute Walk
4. Brushing
5. Direct Manipulation
6. Dynamic Queries

**Interaktionstechiken für visuelle Abbildungen:**

1. Data Flow
2. Pivot Tables

**Interaktionstechniken für Ansichtstransformation:**

1. Direct Selection
2. Camera Movement
3. Magic Lens
4. Overview & Detail
5. Zooming

### 1.8.8 Interaktionskategorien

Kategorien nach Benutzungsabsicht (nicht vollständig):

1. Auswählen
2. Erkunden
3. Neukonfigurieren
4. Entschlüsseln
5. Abstrahieren / Konkretisieren
6. Filtern
7. Verbinden

## 1.9 Zusammenfassung

**Referenzmodell** besteht im Wesentlichen aus vier Phasen:

1. Exploration der Rohdaten
2. Übersetzen der relationalen Daten in visuelle Struktur
3. Ansichtsveränderung
4. Bereitstellung von Mechanismen um Interaktion zu erlauben

**Systematische Modell- und Methodenauswahl**  ist von großer Bedeutung für die erfolgreiche Infromationsvisualisierung
