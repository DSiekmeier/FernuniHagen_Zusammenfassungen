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