# 1 Einführung
Im weitesten Sinne erzeugen **Übersetzer** aus einem Quelltext in der Sprache A ein Zielprogramm der Sprache B. Mindestens die Syntax der Sprache A ist in einer bestimmten Grammatik formuliert.

## 1.1 Anwendungsgebiete
1. Übersetzung einer höheren Programmiersprache in Maschinensprache
2. Dokumentenbeschreibungssprachen wie HTML oder XML
3. Datenbankanfragesprachen wie SQL
4. VLSI-Entwurfssprachen wie VHDL
5. Protokolle in verteilten Systemen

## 1.2 Übersetzungsphasen
Die sechs Phasen der Übersetzung sind logische Schritte müssen aber zeitlich nicht sequentiell ablaufen. Parallel dazu liegt immer die *Verwaltung der Symboltabelle* und die *Behandlung von Fehlern*.

1. Lexikalische Analyse: Ziel ist die Erkennung von Grundsymbolen (Token) aus dem Eingabestrom. Die Struktur der Token kann durch reguläre Ausdrücke beschrieben werden.
2. Syntaxanalyse: Ziel ist die Erkennung von hierachischen Strukturen aus einer Folge von Token. Die Beschreibung kann durch (kontextfreie) Grammatiken erfolgen. Die Ausgabe ist ein Syntaxbaum.
3. Semantische Analyse: Hinzufügen weiterer Informationen, die bei der Syntaxanalyse fehlen, wie Typüberprüfungen und Auflösen überladener Operationen.
4. Erzeugen von Zwischencode: Erstellen von Programmen in einer "abstrakten Maschinensprache" auf höherem Niveau um die Komplexität des Übersetzungsproblems beherrschbar zu machen (Stichwort **3-Adress-Code**). Einfacher, weil vom konkreten Befehlssatz der Zielmaschine abstrahiert wird.
5. Codeoptimierung: Beseitigung der Ineffizienzen die bei der "mechanischen" Zwischencodeerzeugung auftreten können. Erfordert zum Teil sehr komplexe Analysen.
6. Codeerzeugung: Generierung von speziellen Maschinen- oder Assemblercode aus dem optimierten Zwischencode. Herausforderungen sind zum Beispiel Speicherorganisation, Zuteilung von Registern und Optimierung der Befehlsreihenfolge.
