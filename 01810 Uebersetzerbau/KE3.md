## 3.3 Bottom Up-Analyse

Aufbau des Syntaxbaums von den Blättern her nach oben. *Rechte Seiten* der Produktionen werden entdeckt. Nichtterminal auf der linken Seite wird neue Wurzel der Teilbäume.

### 3.3.1 Das Prinzip der Bottom-Up-Analyse

Erkennen von Rechtsableitungen in umgekehrter Reihenfolge. 

    Der Bottom-Up-Parser liest Symbode der Eingabefolge; sobald eine rechte Seite der Produktion komplett vorliegt, wird sie durch das Nichtterminal der linken Seite ersetzt (reduziert).

**Zentrales Problem** ist es zu entscheiden, ob beim Vorliegen einer kompletten rechten Seite reduziert werden soll oder nicht.

**Begriffe:** Handle

**Shift-and-Reduce-Parser** führt vier Arten von Aktionen aus:

1. Shift: Entnehmen des nächsten Symbols und Ablegen auf Stack
2. Reduce:
3. Accept:
4. Error: Entscheide ob ein Syntax-Fehler vorliegt

### 3.3.2 Operator-Vorranganalyse

Ist das schwächste Bottom-Up-Verfahren (nur recht eingeschränkte Klasse von Grammatiken können verarbeitet werden) und ursprünglich für arithmetische Ausdrücke entwickelt. Kann relativ leicht von Hand implementiert werden.
