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

### 3.3.3 LR-Analyse

Mächtigste Klasse von Shift-Reduce-Parsern.

**Vorteile:**

1. Praktisch alle vorkommenden Konstrukte analysierbar
2. allgemeinste Shift-Reduce-Technik ohne Backtracking
3. LR-Parser sind echt mächtiger als LL-Parser
4. Frühstmögliche Erkennung von Eingabefehlern

**Nachteil** sind die von Hand schwer zu konstruierenden Analysetabellen.

**Konstruktion der Tabellen**

Tabelle ist ein endlicher Automat dessen Kanten mit Grammatiksymbolen beschriftet sind.

**Kanonische LR-Parser**

Kleine Steigerung der Leistungsfähigkeit von LR-Parsern durch Nutzen von LR(1)- statt LR(0)-Elementen, also Betrachtung möglicher Folgezeichen.

**Änderungen zu dem SLR-Verfahren**

TODO

**LALR(1)-Parser**

- Zustände miteinander Verschmelzen, dessen Kerne gleich sind um Komplexität zu verringern
- LALR(1)-Tabelle bestimmen, ohne dabei die riesige kanonische LR(1)-Kollektion zu bestimmen
