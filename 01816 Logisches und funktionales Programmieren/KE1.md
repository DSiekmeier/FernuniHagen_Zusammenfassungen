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

##1.3 Beweisstrategie

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