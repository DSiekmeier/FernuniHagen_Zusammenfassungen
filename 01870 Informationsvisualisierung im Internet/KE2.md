# 2 Informationsvisualisierungstechniken I

TODO

## 2.1 Visuelle Strukturen in 1-D, 2-D und 3-D

TODO

### 2.1.1 Eindimensionale Informationsvisualisierungstechniken

- Typische Anwendung bei Visualisierung von Daten aus Textdokumenten und Zeitlinien
- oft in zweidimensionale Informationsvisualisierungstechniken eingebettet
- Schieberegler, Rollbalken, ...
- Beispiel: Seesoft, stellt Zeilen von Programmcodes farblich in Linien dar

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

1. geschachteltes 3D
2. Darstellung auf parallelen Achsen
3. hierachische Anordnung von Einflussgrößen
4. farbkodierte Relevanz
5. aus Venn-Diagrammen synthetisierte Polygone

### 2.4.1 Geschachteltes 3D

*n-vision*-3-D-System benötigt spezielle 3D-Hardware: Wahl eines Punkts im Koordinatensystem fixiert zwei Koordinaten und bildet Ursprung eines weiteren (verschachtelten) Koordinatensystems

Interaktion mit dem System erfolgt durch Datenhandschuh, was für ungeübte Nutzer jedoch zu Fehleingaben führen kann.

### 2.4.2 Darstellung der Dimensionen auf parallelen Achsen

Alle Variablenachsen sind parallel und äquidistant. Fokus der Applikation ist Auffinden von Beziehungen zwischen verschiedenen Variablen.

### 2.4.3 Hierachische Anordnung von Einflussgrößen

TODO

### 2.4.4 Farbkodierte Relevanz hinsichtlich arbiträrer Kriterien

TODO

### 2.4.5 Aus Venn-Diagrammen synthetisierte Polygone

TODO

## 2.5 Informationsvisualisierungstechniken für Baumstrukturen

Zwei grundlegende Arten der Visualisierung von Baumstrukturen / Hierachien:

1. Connection-Methode
2. Enclosure-Methode

### 2.5.1 Die Connection-Methode

- Entspricht dem "gängigen" Bild von Baumstrukturen
- Verwandte Objekte sind miteinander verbunden (im Gegensatz zu Enclosure-Methode wo ein Teilmengenverhältnis visualisiert wird)
- Problem ist die exponentielle Geschwindigkeit mit der der Baum in der Breite wächst

### 2.5.2 Die Enclosure-Methode

TODO

### 2.5.3 Tree-Maps

TODO

### 2.5.4 SeeSys

TODO

### 2.5.5 TennisViewer

TODO

## 2.6 Informationsvisualisierungstechiken für Netzwerke

- Anwendung zum Beispiel bei Kommunikations oder Verkehrsnetzen

### 2.6.1 Methoden zur Knotenpositionierung bei Netzwerkvisualisierungen

1. Positionierung anhand ihrer Position in der Realität
2. **Multidimensionale Skalierung (MDS):** Distanz zwischen Knoten ist umgekehrt proportional zu Kantengewicht
3. **Force-Based:** Knoten werden meist zunächst zufällig positioniert und anschließend mithilfe von "Anziehungskraftbedingungen" in neue Position gebracht
4. **Spring-Based:** Ähnlich wie "Force-Based" jedoch werden die Kräfte zwischen den Knoten iterativ simuliert --> "Einschwingverhalten"

### 2.6.2 Methoden der Interaktion mit Netzwerkvisualisierungen

TODO

### 2.6.3 Anwendungsbeispiele zur Visualisierung von Netzwerken

**SemNet**

**HierNet**

**SeeNet**

## 2.7 Informationsvisualisierungstechniken für Dynamische Anfragen

**Motivation:** Daten müssen nicht nur visualisiert werden, sondern auch Informationen effizient aus einer großen Menge von Daten extrahiert werden können.

Dies ist zwar mit SQL etc. möglich, jedoch ist hier eine höhere Einarbeitungszeit notwendig.

Neue / unerfahrene Benutzer sollen sich Informationen mithilfe von **visuell-direkmanipulativen** Anfragen erschließen können.

Dynamic Queries ermöglichen jedoch nur eine UND-Verknüpfung der Bedingungen.

### 2.7.2 Das Grundkonzept Dynamischer Anfragen

Merkmale sind

- direktmanipulative Auswahl geeigneter Anfrageparameter
- keine spezielle, formale Anfragesprache notwendig
- Ergebnisse werden sofort visualisiert 
- Enge Kopplung ermöglicht "Echtzeit" (siehe psychologischer Moment)
- "Output-is-Input"

### 2.7.2 Interaktion mit Dynamischen Anfragen

> Zentrales Konzept hinter Dynamic Queries ist die enge Kopplung zwischen Interaktions- und Informationsvisualisierungskomponente.

Liste der Interaktionstechniken für **Datentransformationen**

1. Direkt Walk
2. Details-on-Demand
3. Attribute Walk
4. Brushing
5. Direct Manipulation
6. Dynamic Queries

Liste der Interaktionstechniken für **visuelle Abbildungen**

1. Data Flow
2. Pivot Tables

Liste der Interaktionstechniken für **Ansichtentransformationen**

1. Direct Selection
2. Camera Movement
3. Magic Lens
4. Overview and Detail
5. Zooming

### 2.7.3 Dynamic-Query-Anwendungen

TODO

### 2.7.4 Zusammenfassung

- Hervorragende Eignung um große Datenmengen in kurzer Zeit zu untersuchen
- Dynamic Queries helfen schwierige Anfragen zu stellen
- Dynamic Queries nutzen die visuelle Wahrnehmungsfähigkeit des Menschen sehr gut aus
