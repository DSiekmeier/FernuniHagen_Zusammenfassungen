# 5 Basistechnologien Rendering, VRML und X3D - Teil 1: Grundkonzepte, Animation und Interaktion

## 5.1 Exkurs in die Computergrafik

> **Rendering** ist die Erzeugung eines zweidimensionalen Bildes aus einem mehrdimensionalen, mathematischen Modell. Dieses Modell beschreibt eine dreidimensionale Szene mithilfe einzelner Komponenten.

Wichtige Kriterien für die Qualität der Bildezeugung sind **Naturalismus** und **Geschwindigkeit** (Bilderzeugung für Interaktion sollte unterhalb der *Flimmerfusionsfrequenz* liegen, etwa 15 Hz).

### 5.1.1 Grundkonzepte und Kategorien von Renderingsystemen

Die Szene wird in geeignete geometrische **Primitive** zerlegt, mit dem Ziel der vollständigen Darstellbarkeit und effizienten Berechnung.

Renderingelemente:

1. Linien und Polygone (meist in Dreiecke unterteilt); durch Texturen verschönert
2. Partikelsysteme
3. Voxel
4. Lichtquellen und Kamera

### 5.1.2 Interaktion zwischen Szenenelementen beim Rendering

TODO

### 5.1.3 Renderingalgorithmen

TODO

### 5.1.4 Unschärfe

TODO

### 5.1.5 Beleuchtung

TODO

### 5.1.6 Pixars Photorealistic RenderMan

TODO

### 5.1.7 Open GL

TODO

### 5.1.8 Open Inventor

TODO

### 5.1.9 Historie von VRML im Überblick

> VRML steht für **V**irtual **R**eality **M**odeling **L**anguage und ist ein Dateiformat zur Beschreibung von interaktiven 3-D-Objekten und -Welten. Möglich sind komplexe Szenen mit Benutzereingaben, Weiterleitungen durch Links, Animationen, ...

1994: erster Entwurf jedoch ohne Animationen, Sensoren, Töne und Ereignismodell

1997: Nachfolger VRML2 ist noch heute konzeptionell in X3D, Java3D, ... enthalten

### 5.1.10 VRML1.0

- Vorlage war das *Open Inventor*-Dateiformat mit dem bekannten Szenengraph-Konzept
- größtest Manko: keine Engines und Feldverknüpfungen, dadurch keine Bewegung und Interaktivität
- es folgten viele proprietäre Erweiterungen

### 5.1.11 VRML2.0

- Bis auf den Namen und dem Szenengraf nur noch wenige Gemeinsamkeiten mit dem Vorgänger
- Szenen und Welten werden durch **hierachischen Szenengraf** beschrieben
- es stehen etwas **50 Knotentypen** zur Verfügung
- durch **Prototyping-Mechanismus** können neue Knoten hinzugefügt werden
- es existiert ein **Erweiterungsmodell**

Anforderungen an die Entwicklung waren:

1. Performanz
2. Erweiterbarkeit
3. Implementierbarkeit / Plattformunabhängigkeit
4. Multi-User-Potential
5. Skalierbarkeit
6. Authorability
7. Vollständigkeit
8. Kombinierbarkeit
9. Orthogonalität
10. Wohlstrukturiertheit

- räumliche Sound-Knoten
- Sensorknoten
- Interpolatoren
- Skript-Knoten

Verarbeitung der VRML-Datei:

1. Parser erstellt Szenen- und Routengraph
2. Execution Engine überwacht die beiden Graphen
3. Benutzereingaben werden mit Routengraph ausgewertet oder wirken direkt auf die Szene (z.B. durch Menüleisten)

### 5.1.12 X3D

> X3D ist die Bestrebung den VRML-Standard mit XML zu harmonisieren. X3D ist eine strikte Untermenge der VRML-Spezifikation. Die Erweiterungs-API (SAI, Scene Authoring Interface) ist sehr mächtig.

Die Konzepte in X3D entsprechen denen von VRML, jedoch im Umfang eingeschränkt. Statt Scripting- und Prototyping-Mechanismen wird die SAI genutzt und der Funktionsumfang durch Profile erweitert.

### 5.1.13 Kodierung von VRML2.0- und X3D-Dateien

TODO

### 5.1.14 Unterschiede zwischen VRML1.0 und VRML2.0/X3D

TODO

### 5.1.15 Die Datentypen von VRML2.0 / X3D

TODO

### 5.1.16 Unterschiede in der Kodierung von VRML1.0- und VRML2.0 / X3D-Dateien

TODO

### 5.1.17 Der Aufbau von Knoten in VRML2.0 / X3D

- Knotenname
- beliebige Anzahl von Feldern und Ereignissen
- öffentliche Schnittstelle
- Jedes Feld hat Default-Value
- Schlüsselwörter: eventIn, eventOut, field, exposedField

### 5.1.18 Klassen von Knotentypen in VRML

> Es gibt drei **Klassen von Knotentypen**: unabhängige Knoten, Gruppenknoten und Blattknoten die noch feiner untergliedert werden können.

1. unabhängige Knoten
2. Gruppenknoten
3. Blattknoten (grafisch und nichtgrafisch)

### 5.1.19 Grafische Blattknoten

Grafische Blattknoten werden unterteilt in:

1. **Geometrieknoten:** Box, Cone, Cylinder, Text, ...
2. **Attributknoten:** Appearance, Color, Material, FontStyle, ...

### 5.1.20 Nichtgrafische Blattknoten

TODO
