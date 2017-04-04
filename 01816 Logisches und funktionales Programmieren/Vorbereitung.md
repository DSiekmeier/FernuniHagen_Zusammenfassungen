# Logisches Programmieren

**L1) Was ist das Besondere an den im Kurs vorgestellten Sprachen?**
Beide Sprachen gehören zu den deklarativen Sprachen. Eine Besonderheit ist, dass eher das "Was" als das "Wie" der Problemlösung beschrieben wird. Die entstehenden Programme sind oft kürzer und abstrakter und in der Regel frei von Seiteneffekten.

**L2) Woraus besteht ein Prolog-Programm**
Ein Prolog-Programm besteht aus einer Datenbasis und Anfragen die darauf gestellt werden. Die Datenbasis besteht aus Klauseln, die in Fakten und Regeln unterteilt sind. Fakten sind elementare Tatsachen über ein zu lösendes Problem und haben die Form

	wertvoll( gold ) .

*wertvoll* ist eine Eigenschaft und wird Prädikat genannt. Die Ausdrücke in den Klammern heißen Argumente. Die Anzahl der Argumente ist die Stelligkeit. Fakten können als Regeln intepretiert werden die immer wahr sind.

Regeln dienen dem Ableiten neuer von vorhandenen Tatsachen und haben die Form

	L0 :- P1, P2, ... , Pn.

Die rechte Seite besteht aus einer Konjunktion von Prämissen, die linke Seite ist die Konklusion.

Anfragen haben die gleiche Form wie die rechte Seite von Regeln, bestehen also aus einem oder mehreren Literalen. Diese müssen im Gegensatz zur Datenbasis aber nicht wahr sein.

**L3) Wie wird eine Anfrage *Q1, Q2, Q3* bewiesen?**
Grundlage zum Beweisen ist das allgemeine Resolutionsprinzip anhand dessen ein zur Anfrage passender Klauselkopf in der Datenbank gesucht wird. Die Klauseln werden dabei von oben nach unten durchsucht, die zu beweisenden Literale im Rumpf der Anfrage von links nach rechts.

In der Regel ist eine Anfrage nicht direkt beweisbar, da sie zum Beispiel Variablen enthält. Die Unifikation ist ein Prozess, der eine Substitutionsfunktion für eine Variable berechnet, damit ein Klauselkopf auf die Anfrage passt. Hierzu existiert ein Unifikationsalgorithmus, der den allgemeinsten Unifikator berechnen kann.

**L4) Was ist Backtracking?**
Allgemein ist Backtracking ein Algorithmus, der ausgehend von Teillösungen eine Gesamtlösung sucht. Führt eine Teillösung in eine Sackgasse so wird eine alternative Lösung ausprobiert, bis keine Alternativen mehr vorhanden sind (Trial-and-Error).

**L5) Welche nicht-logischen Komponenten gibt es in Prolog?**
Das Backtracking-Verfahren, da dies nicht parallel ausgeführt wird, Cut-Operator, Negation \\+, Arithmetik, Ein- und Ausgabe-Funktionen da diese Seiteneffekte haben, ...

**L6) Wie funktioniert der Cut-Operator?**
Der Cut-Operator, dargestellt als Atom !, dient der Begrenzung des Suchraums indem das Backtracking-Verfahren beeinflusst wird. Der Cut-Operator kann in Anfragen oder auf der rechten Seite von Regeln auftreten und ist logisch gesehen immer beweisbar. Die Grundform in einer Regel ist wie folgt:

	p :- q, !, r.

Beim Feuern der Regel können zwei Alternativen auftreten:

1. q ist nicht beweisbar: Der Cut-Operator hat keine Bedeutung und es wird die nächste Klausel für p gesucht.

2. q ist beweisbar: Dann ist p nur beweisbar wenn r mit den Bindungen von q beweisbar ist. Schlägt dies fehl, dann wird abgebrochen und keine Alternative für p gesucht.

Also: zunächst wird q bewiesen. Ist dies nicht erfolgreich wird wie üblich das Backtracking weitergemacht. Wenn q bewiesen werden kann, werden die Variablen unifiziert und r mit diesen Variablenbindungen bewiesen. Wenn dies erfolgreich ist, ist p bewiesen. Schlägt der Beweis von r mit Bindung von q fehl, dann wird der Suchraum duch ! beschnitten und es wird keine Alternative für p gesucht.

Cut-Operator kann als Fallunterscheidung eingesetzt werden:

	p :- q, ! , r.
	p :- s.

> IF q THAN r ELSE s.

**L7) Was ist ein Akkumulator?**
Ein Akkumulator ist ein zusätzliches Argument in einem Prädikat, das dazu dient Zwischenergebnisse zu speichern.

**L8) Welche typischen Programmiertechniken gibt es in Prolog?**7

**1. Programmieren mit Akkumulatoren:** Eine Klausel besteht aus mindestens drei Argumenten: eins für die Eingabe, eins als Zwischenergebnis (Akkumulator) und eins als Ergebnis. Das Ergebnis wird schrittweise aufgebaut, während die Eingabe immer kleiner wird. Beispiel ist das Prädikat *reverse/2*.

**2. Suchen nach allen möglichen Lösungen:** Ist geeignet wenn keine systematische Vorgehensweise für die Lösungsfindung bekannt ist. Hier werden alle möglichen Lösungen generiert und anschließend getestet (Generate-and-Test). Das prinzipielle Vorgehen ist:

	loesung( L ) :- potentielleLoesung( L ), korrekteLoesung( L ). 

**3. Musterorientierte Programmierung:** Entspricht in gewisser Weise dem Gegenteil von 2, da die Klauselköpfe so aufgebaut werden, dass immer nur eine Klausel angewendet werden kann. Dies erhöht die Effizienz. Beispiel ist das Prädikat *sortiert/1*.

**4. Relationale Programmierung:** Da nicht festgelegt ist, welche der Argumente in einer Anfrage mit einem Grundterm belegt ist und welche nicht, kann für eine Funktion auch immer die Umkehrfunktion berechnet werden. Beispiel ist das Prädikat *append/2*, welches auch zum Zerlegen zweier Listen genutzt werden kann.

# Funktionale Programmierung
**F1) Was ist funktionale Programmierung?**
In der FP werden Programme aus Funktionen zusammengesetzt. Kennzeichnend sind hier Konzepte wie das Fehlen von Seiteneffekten (Pure Functions) so dass auf innere Zustände eines Berechnungsprozesses verzichtet werden kann und Funktionen höherer Ordnung, also Funktionen die sowohl als Ergebnis als auch als Argument anderer Funktionen auftreten können (Funktionen sind gleichberechtigte Datentypen).

# Constraint logische Programmierung