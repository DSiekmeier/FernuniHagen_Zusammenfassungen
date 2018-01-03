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

## 1.3 Die Systemumgebung des Compilers
1. Präprozessor: Überführt den Quellcode in eine vom Compiler akzeptierte Form. Reicht von einfachen Textersetzungen bis zu komplexeren Makros.
2. Compiler: Erzeugt das Zielprogramm in Assemblersprache
3. Assembler: Erzeugt verschiebbares Programm in Maschinensprache. Assemblersprache ist nah an der Maschinensprache und definiert Mnemonics.
4. Linker: Baut eine Menge von verschiebbaren Maschinenprogrammen zu einem ausfühbaren Programm zusammen und löst externe Referenzen auf.
5. Loader: Rechnet die relativen Adressen im verschiebbaren Programm in Absolute um und läd die Anwendung in den Speicher.

## 1.4 Compiler und Interpreter, reale und abstrakte Maschinen
Interpretation eines Programms ist Alternative zum Compilieren. Anstatt der Synthese (beim Compiler) tritt die direkte Ausführung der Befehle.

Vorteile: schnellere Programmentwicklung (sofort ausführbar)

Nachteil: Analyse muss immer wieder gemacht werden

Beide Ansätze sind durch eine Zwischensprache kombinierbar (vgl. Byte-Code in JAVA): Compiler übersetzt von Quellsprache A in Zielsprache B die von einem Interpreter in die Maschienensprache X für die reale Hardware ausgeführt wird.

Vorteil: Programme sind portable wenn Interpreter für die Zielmaschine existiert, die Ausführung der Zwischensprache B kann auf einer *abstrakten Machine* mit anderen Fähigkeiten wie der realen Hardware passieren (z.B.: Stackmaschine).

## 1.5 Werkzeuge
Für die Lösung der Teilaufgaben lassen sich präzise Spezifikationen angeben, was das Erstellen und Nutzen von Werkzeugen ermöglicht. Beispielsweise

- Scannergenratoren (z.B.: Lex)
- Parsergeneratoren (z.B.: YACC)
- Generatoren für abstrakte Syntaxbäume
- Generatoren für Attributauswerter
- Transformation abstrakter Syntaxbäume
- Generatoren für Codegeneratoren

Scanner und Parser arbeiten in der Regel "Hand in Hand", d.h, der Parser fordert ein Token an und der Scanner liefert es. --> Nicht zwangsläufig sequentiell.

# 2 Lexikalische Analyse
Die lexikalische Analyse ist die erste Phase mit dem Ziel der Umwandlung des Eingabe-Zeichenstroms in "atomare" Einheiten (**Token**) für den Parser.

Lexikalische Symbole können durch reguläre Ausdrücke oder Zustandsdiagramme (endliche Automaten) dargestellt werden.

**Theoretische Hintergründe**

1. Struktur lexikalischer Symbole kann durch reguläre Ausdrücke beschrieben werden.
2. Reguläre Sprachen werden durch rechtslineare oder linkslineare Grammatiken erzeugt.
3. Sie werden durch nichtdeterministische endliche Automaten erkannt.
4. Zu jedem nichtdeterm. endl. Automaten kann ein deterministischer endlicher Automat konstruiert werden.

## 2.1 Beschreibung von Token durch reguläre Ausdrücke
**Begriffe:** Alphabet, Wörter, leeres Wort, Sprache, Konkatenation, Vereinigung, Abschlussoperation

**Vereinfachte Notation von reg. Ausdrücken:**

1. "+": ein- oder mehrfaches Auftreten des vorangegangenen Symbols
2. "?": optionales Auftreten
3. "Zeichenklassen [axf9]": einmaliges Auftregen eines der Zeichen

## 2.2 Beschreibung von Token durch Zustandsdiagramme
Grafische Notation für deterministische endliche Automaten definiert durch die Menge M = (Q, Sigma, delta, s, F)

1. Q: endliche nichtleere Menge von Zuständen
2. Sigma: Alphabet von Eingabezeichen
3. delta: Q x Sigma -> Q ist Übergangsfunktion
4. s Element von Q: Anfangszustand
5. F Teilmenge von Q: Menge von Endzuständen

In jedem Schritt wird ein Zeichen gelesen und ein neuer Zustand eingenommen, bestimmt durch *delta*. Wenn ein Zustand F erreicht wird, ist die Zeichenfolge akzeptiert.

## 2.3 Direkte Implementierung eines Scanners
TODO

## 2.4 Implementierung eines Scanners mit Lex
Lex liest Spezifikation aus einer Datei *lex.l* und generiert das C-Programm *lex.yy.c* welches kompiliert und gegen eine Anwendung gelinkt werden kann. Die Funktion
    
    int yylex()

liefert bei jedem Aufruf ein Token. Die Spezifikation besteht aus drei Teilen: Deklarationen, Tokendefinitionen und Aktionen, Hilfsprozeduren.

    Deklarationen
    %%
    Tokendefinitionen und Aktionen
    %%
    Hilfsprozeduren

Der generierte Analysator akzeptiert bei Mehrdeutigkeit immer ein Token maximaler Länge.
