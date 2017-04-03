# Logisches Programmieren

**1) Woraus besteht ein Prolog-Programm**
Ein Prolog-Programm besteht aus einer Datenbasis und Anfragen die darauf gestellt werden. Die Datenbasis besteht aus Klauseln, die in Fakten und Regeln unterteilt sind. Fakten sind elementare Tatsachen über ein zu lösendes Problem und haben die Form
	
	wertvoll( gold ) .
	
*wertvoll* ist eine Eigenschaft und wird Prädikat genannt. Die Ausdrücke in den Klammern heißen Argumente. Die Anzahl der Argumente ist die Stelligkeit. Fakten können als Regeln intepretiert werden die immer wahr sind.

Regeln dienen dem Ableiten neuer von vorhandenen Tatsachen und haben die Form

	L0 :- P1, P2, ... , Pn.

Die rechte Seite besteht aus einer Konjunktion von Prämissen, die linke Seite ist die Konklusion.

Anfragen haben die gleiche Form wie die rechte Seite von Regeln, müssen aber nicht wahr sein.

**2) Wie wird eine Anfrage *Q1, Q2, Q3* bewiesen?**
Grundlage zum Beweisen ist das allgemeine Resolutionsprinzip anhand dessen ein zur Anfrage passender Klauselkopf in der Datenbank gesucht wird. Die Klauseln werden dabei von oben nach unten durchsucht, die zu beweisenden Literale im Rumpf der Anfrage von links nach rechts.

In der Regel ist eine Anfrage nicht direkt beweisbar, da sie zum Beispiel Variablen enthält. Die Unifikation ist ein Prozess, der eine Substitutionsfunktion für eine Variable berechnet, damit ein Klauselkopf auf die Anfrage passt. Hierzu existiert ein Unifikationsalgorithmus, der den allgemeinsten Unifikator berechnen kann.

**3) Was ist Backtracking?**
Allgemein ist Backtracking ein Algorithmus, der ausgehend von Teillösungen eine Gesamtlösung sucht.

**4) Wie funktioniert der Cut-Operator?**
Der Cut-Operator, dargestellt als Atom !, dient der Begrenzung des Suchraums indem das Backtracking-Verfahren beeinflusst wird.