# 1 Motivation und Einführung

**Ziel der Informationsvisualisierung:** Repräsentation abstrakter Daten, so dass
strukturelle Zusammenhänge und relevante Eigenschaften intuitiv erfasst werden können

## 1.1 Ursprünge und Entwicklung der IV

- erste Arbeiten bereits 1786
- mit Aufkommen leistungsfähiger 3D-Hardware erste Visualisierungsansätze für abstrakte Daten
- Ergänzung um Echtzeitanimation und -interaktion

## 1.2 Informationsdialoge - Mensch-Maschine-Interaktion mit Inforationssystemen

Informationsmengen am Beispiel eines Suchvorgangs im Internet:

1. Die **Inhaltsmenge** ist die Menge der **Informationsobjekte** (Daten, Dokumente, ...) die das Informationssystem anbieten kann
2. Die **Interessenmenge** ist diejenige Menge der Informationsobjekte, die geeignet sind um das **Informationsbedürfnis** (um eine Aufgabe zu erfüllen oder ein Problem zu lösen) des Anwenders zu erfüllen
3. Die **Relevanzmenge R** ist der Schnitt aus Inhaltsmenge (vom System) und Interessenmenge (vom Nutzer)
4. Durch verschiedene Suchanfragen können meherer **Ergebnismengen** entstehen, die jedoch einen Schnitt zwischen Inhaltsmenge und Relevanzmenge bilden
5. Die Ergebnismengen überlappen sich in der Praxis nicht vollständig mit der Relevanzmenge, daher wird der Schnitt zwischen allen Ergebnismengen häufig **Kernmenge** genannt

## 1.3 Modelle zur Informationsvisualisierung

Informationsvisualisierung ist im Wesentlichen ein Abbildungsprozess. Ursprungsdaten werden umgewandelt und auf visuelle Objekte abgebildet.

Das **Referenzmodell der Informationsvisualisierung** beschreibt den Transformationsprozess konzeptionell.

- Rohdatenmenge liegt als Datensatz vor
- wird im ersten Schritt auf strukturierte Daten reduziert
- Datenmodell und Datenschema wird mit Visualisierungsmodell und Visualisierunsschema in Verbindung gebracht
- die entstandenen visuellen Strukturen so transformiert werden, dass Sichten entstehen

Das Referenzmodell geht davon aus, dass die Rohdaten als relationale, strukturierte Daten vorliegen.

Es existiert ein neueres Modell nach Chi und Riedel, welches die Transformationsschritte klarer definiert und abgrenzt.

## 1.4 Daten- und Datentransformation

Transformation kann auf viele Arten geschehen: Filtern, Gruppieren, Hinzufügen von Meta-Daten, ...

## 1.5 Visuelle Abbildung

Die **visuelle Abbildung (Mapping)** ist der entscheidende Schritt bei der Informationsvisualisierung. Eine gute visuelle Abbildung ist expressiv (ausdrucksstark) und effektiv. Sie bedient sowohl bewusste als auch unbewusste kognitive Vorgänge. Die Abbildungen sollten möglichst so gewählt werden, dass Verständnis und Wahrnehmung weitestegehend unbewusst abgewickelt werden kann.

### 1.5.1 Strukturabbildungen

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

Zweite wesentliche Komponente bei visuellen Abbildungen: Punkte, Linien, Flächen, Quader, ...

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

1. **Phase:** Paralleles Extrahieren von einfachen Eingenschaften der visuellen Szene
2. **Phase:** Musterwahrnehmung
3. **Phase:** Sequentielle und zielgerichtete Verarbeitung

### 1.6.3 Elementare visuelle Wahrnehmung

Vier Gruppen von Wahrnehmungseigenschaften:

1. assoziative Wahrnehmung 
2. selektive Wahrnehmung
3. Wahrnehmung der Anordnung
4. quantitative Wahrnehmung

- Erste Phase der Informationsverarbeitung wird auch **präattentiv** genannt und geschieht bevor Aufmerksamkeit des Benutzers aktiv auf Details gerichtet wird.
- ist unabhängig vom Stresslevel der Person
- visuelle Attribute die präattentiv sind: Form, Farbe, Bewegung räumliche Position in jeweils verschiedenen Ausprägungen

### 1.6.4 Zeitschranken der Ausprägung

- große Änderungen an einer Informationsvisualisierung werden nicht wahrgenommen: **Änderungsblindheit**
- tritt auf bei zeitglichen, irrelevanten Änderungen

Drei zeitabhängige Stufen der Wahrnehmung:

1. Psychologisches Moment (0,1 Sekunden)
2. Unvorbereitete Rückmeldung (1 Sekunde)
3. Aufgabeneinheit (10 Sekunden)

### 1.6.5 Kongnitionsunterstützung und kognitive Verstärkung

**Kognitionsunterstützung:** Unterstützung menschlicher "Denkleistung"

**externe Wahrnehmung:** TODO

**kognitive Kosten:** TODO

## 1.7 Begriff der Informationsvisualisierung

> **Visualisierung** ist der Gebrauch computerunterstützter interaktiver visueller Darstellungen von Daten um Verständnis zu erleichtern.

Im Kurs:

> **Informationsvisualisierung** ist der Gebrauch von computergestützten interaktiven, visuellen Darstellungen von abstrakten Daten, um deren Zugriff Wahrnehmung, Interpretation und Verständnis zu erleichtern.

--> Unterscheidung in Beschaffenheit der Daten: abstrakte Daten haben naturgemäß keine physische Erscheinungsform.

## 1.8 Interaktionen und Interaktionstechniken

TODO
