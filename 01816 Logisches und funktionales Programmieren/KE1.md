#1 Logisches Programmieren
##1.1 Einleitung
Prolog basiert auf der Prädikatenlogik 1. Ordnung, konkret der logischen Beschreibung eines Problems in Form von Fakten und Regeln (Klauseln). Aufgrund der Klauseln "berechnet" das Prologsystem die Lösung (Backtracking-Algorithmus).

##1.2 Syntax von Prolog
###1.2.1 Datentypen
>"Ein Term ist entweder eine Konstante (Zahl oder Atom), eine Variable oder eine Struktur, deren Komponenten wieder Terme sind. Ein Term heißt *Grundterm* wenn er keine Variablen enthält."

**Term**: allgemeine Form von Objekten. Oberbegriff für die restlichen Typen. 
**Konstante**: Oberbegriff für Zahl und Atom 
**Zahl**: Folge von Ziffern 
**Atom**: Zeichenfolge mit bestimmten Aufbau-Regeln 
**Variable**: beginnt mit Großbuchstaben 
**Struktur**: Objekt, zusammengesetzt aus anderen Objekten 

###1.2.2 Operatoren
Jeder Operator hat eine
- **Position** (Präfix, Infix, Postfix)
- **Assoziativität** (links- oder rechtsassoziativ)
- **Präzedenz / Rangfolge** (Operator mit kl. Präzedenz bildet Unterstruktur)

###1.2.3 Listen
Im Gegensatz zu Strukturen sind bei Listen die Anzahl der Elemente im Voraus unbekannt. Eine Liste ist entweder

1. eine leere Liste, dargestellt durch das Atom [ ]
2. eine Struktur mit Funktor . und zwei Komponenten, wobei die zweite eine Liste ist

Beispiele für Listen (mit *Listennotation*):

- [ ] entspricht [ ]
- .(x, [ ]) entspricht [x]
- .(x, .(y, [ ])) entspricht [x, y]

Listen können in Listenkopf und Listenrest unterteilt werden: [ a | [b, c] ]

*Texte* entsprechen Folgen von Zeichen in Liste: [80, 114, 111, 108, 111, 103]

###1.2.4 Fakten, Regeln und Anfragen
Darstellung von Wissen in Prolog in zwei Formen möglich:

1. **Fakten**: Tatsachen über Eigenschaften von Objekten und deren Beziehungen
2. **Regeln**, zum Ableiten neuer Tatsachen

Fakten haben ein Atom als Namen: *eltern*(christine, heinz, angelika).

Regeln haben die Form von "Wenn-Dann"-Aussagen: geschwister(K1, K2) :- eltern(M, V, K1),eltern(M, V, K2). Allgemein: L_0 :- L_1, ..., L_n. Die Aussagen haben dieselbe Form wie Fakten und werden darum zur Unterscheidung **Literale** genannt.

>"Fakten können als Regeln ohne Voraussetzungen aufgefasst werden."

Weitere **Begriffe**:

1. Prädikat: Funktion die wahr / falsch als Wert liefert ( *weiblich*(anne). ) 
2. Stelligkeit: Anzahl der anzugebenden Objekte
3. Klauseln: allgemeiner Oberbegriff für Fakten und Regeln 

##1.3 Beweisstrategie
###1.3.1 Prinzip der Resolution
Das **allgemeine Resolutionsprinzip** findet immer eine Lösung wenn sie existiert.

**Modus ponens / Abtrennungsregel:**

>"Wenn jedes der Literale L_1, ..., L_n beweisbar ist, und L_0 :- L_1, ..., L_n. eine Regel ist, dan ist auch das Literal L_0 beweisbar."

**Resolutionsprinzip:**

>"Ist L_0 :- L_1, ..., L_n. eine Regel, dann ist das Literal L_0 beweisbar, wenn jedes der Literale L_1, ..., L_n beweisbar ist."


Die Aussage der beiden Regeln ist äquivalent, unterscheidet sich jedoch in der Sichtweise. Zunächst wird eine Regel gesucht, deren linke Seite mit dem Literal übereinstimmt und anschließend wird versucht die Regeln der rechten Seite zu beweisen.

Das *allemeine Resolutionsprinzip* berücksichtigt zusätzlich das Ersetzen von Variablen sowie die Tatsache, dass in der Regel eine Menge von Literalen bewiesen werden muss.

###1.3.2 Unifikation
**Unifikation** ist der Prozess des Ersetzens von Variablen in einem Resolutionsschritt. Gleiche Variablen werden immer durch gleiche Terme ersetzt. Jede Substitution ändert nur eine Variable. Schreibweise \sigma = {N/meier, A/55}

Aus dem **allgemeinsten Unifikator** ist jeder andere Unifikator ableitbar. Es ist wichtig den allgemeinsten Unifikator nicht zu speziell zu wählen um beim allgemeinen Resolutionsprinzip nicht in eine Sackgasse zu laufen.

**Algorithmus zur Unifikation**
siehe Skript (fünf Fälle)

Werden zwei Strukturen miteinander unifiziert, werden die Komponenten paarweise unifiziert.

In der Praxis verzichten viele Prolog-Systeme aus Effizientgründen auf den **Vorkommenstest**.

###1.3.3 Backtracking

##1.4 Programmiertechniken
###1.4.1 Programmieren mit Akkumulatoren
Formulierung rekursiver Prädikate die auf rekursive Termstrukturen arbeiten, in der Art, dass die zu bearbeitende Termstruktur kleiner wird und die Ergebnismenge wächst. Das Problem ist gelöst, wenn die  Ausgangsstruktur vollständig abgebaut ist.

**Beispiel:**

	reverse( L, A ) :- rev( L, [ ], A ).
	rev( [ ], A, A ).
	rev( [H|L], R, A ) :- rev( L, [H|R], A ).

###1.4.2 Suchen nach allen möglichen Lösungen

**Beispiel:**

	loesung( L ) :- potentielleLoesung( L ), korrekteLoesung( L ).

###1.4.3 Musterorientierte Programmierung
- Gegenteil zur "Suche nach allen möglichen Lösungen"
- da es hier meist nur eine Lösung gibt.

**Beispiel:**

	sortiert( [ ] ).
	sortiert( [E] ).
	sortiert( [E1, E2|R] ) :- E1 =< E2, sortiert( [E2|R] ).

###1.4.4 Relationale Programmierung
Das Prädikat wird als Relation definiert:
	
	f( X_1, ..., X_n, Y).

Da Prolog nicht festlegt, welches Literalargument mit einem Grundterm belegt werden muss und welches nicht, ist auch eine _Umkehrfunktion_ berechenbar.