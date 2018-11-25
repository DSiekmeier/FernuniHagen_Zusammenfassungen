# 2 Informationsvisualisierungstechniken I

- Unterteilung der Techniken in verschiedene Klassen

## 2.1 Visuelle Strukturen in 1-D, 2-D und 3-D

### 2.1.1 Eindimensionale Informationsvisualisierungstechniken

- häufig Daten aus Textdokumenten und Zeitlinien
- oft in zweidimensionale Informationsvisualisierungstechniken eingebettet
- Schieberegler, Rollbalken, ...

### 2.1.2 Zweidimensionale Informationsvisualisierungstechniken

- häufig für Darstellung von relational strukturierten Datensätzen
- Daten mit topologischen oder geografischen Eigenschaften
- Beispiel: Scatter Plots (nur zwei Datencharakteristiken je Informationsobjekt)
- zusätzliche Informationen zum Beispiel durch Farbkodierungen

### 2.1.3 Dreidimensionale Informationsvisualisierungstechniken

- gegeignet für Visualisierung im Zusammenhang mit real existierenden Objekten
- Darstellung kann mit abstrakten Informationen angereichert werden

### 2.1.4 Vergleich zwischen 2D- und 3D-Informationsvisualisierungstechniken

- 3D sehr ausdruckstart und vom Nutzer oft als ansehnlich empfunden
- 3D gut geeignet für physische Objekte
- jedoch vergleichsweise hoher Rechenbedarf (Beleuchtung, Textur, Verdeckung, ...)

## 2.2 Automatisierung der Konstruktion von Informationsvisualisierungen in 2D

**Ziel:** Informationsvisualisierungstechnik die eine hohe Anzahl von Datencharakteristiken visualisiert

- Scatter Plots nur für maximal *drei* Datencharakteristiken

TODO

### 2.2.1 Ansatz zur automatischen Generierung von grafischen Präsentationen in 2-D

1. Daten werden aus relationaler Datenbank abgefragt
2. Werkzeug synthetisiert aus diesen Daten ein grafisches Design
3. Werkzeug generiert ein Bild gemäß den Designvorgaben

### 2.2.2 Expressivität und Effektivität von Präsentationen

Visualisierung ist **expressiv** wenn wenn sie die gesamten relevanten, und zwar nur diese, anzeigt.

Visualisierung ist **effektiv** wenn sie die Möglichkeiten des Ausgabemediums und die visuellen Fähigkeiten des Menschen nutzt.

Formale Repräsentation dieser Kritierien durch das Konzept **grafischer Sprachen**, die aus grafischen Sätzen besteht.

Expressivität grafischer Sprachen ist von Syntax und Semantik der Sprache abhängig. Effiktivität ist auch abhängig von visuellen Fähigkeiten der Nutzer --> Nutzen von empirischen Daten aus der Forschung.

### 2.2.3 Funktionsweise des Präsentationswerkzeugs APT (A Presentation Tool)

Vier Arbeitsschritte um aus Tupeln einer relationalen Datenbank eine grafische Repräsentation zu generieren:

1. Partitionierung
2. Selektion
3. Komposition
4. Bildgenerierung

## 2.3 Animation in 3-D-Informationsvisualisierungstechniken

- Expressivität und Effektivität auch auf dreidimensionale Bilder übertragbar, jedoch bei Expressivität völlig neue Möglichkeiten
- Problem: Informationen im Hintergrund können verdeckt werden (Verstoß geggen Expressivität)
- Problem: visuelle Darstellung teilweise nicht eindeutig (Größen zu Beispiel Blickpunkt abhängig)

## 2.4 Informationsvisualisierungstechniken für mehr als drei Dimensionen

- geschachteltes 3D
- Darstellung auf parallelen Achsen
- hierachische Anordnung von Einflussgrößen
- farbkodierte Relevanz
- aus Venn-Diagrammen synthetisierte Polygone

### 2.4.1 Geschachteltes 3D

*n-vision*-3-D-System benötigt spezielle 3D-Hardware: Wahl eines Punkts im Koordinatensystem fixiert zwei Koordinaten und bildet Ursprng eines weiteren (verschachtelten) Koordinatensystems

Interaktion mit dem System erfolgt durch Datenhandschuh, was für ungeübte Nutzer jedoch zu Fehleingaben führen kann.

### 2.4.2 Darstellung der Dimensionen auf parallelen Achsen

Alle Variablenachsen sind parallel und äquidistant. Fokus der Applikation ist Auffinden von Beziehungen zwischen verschiedenen Variablen.