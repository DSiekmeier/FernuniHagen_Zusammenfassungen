# 3 Syntaxanalyse

Syntaxanalyse ist zweite Phase der Übersetzung mit dem Ziel aus der Tokenfolge vom Scanner einen Syntaxbaum (auch Ableitungsbaum) zu erstellen. Basis ist die *Grammatik* die die Syntax der Quellsprache beschreibt.

Es werden zwei Vorgehen unterschieden:

**1. Top-Down-Analyse:** Der Baum wird von der Wurzel aus aufgebaut, beginnend vom Startsymbol der Grammatik.

**2. Bottom-Up-Analyse:** Der Baum wird von den Blättern her aufgebaut indem solange Token eingelesen werden, bis eine vollständige rechte Seite der Grammatik vorliegt.

## 3.1 Kontextfreie Grammatiken und Syntaxbäume

TODO

**Begriffe:** Links- und Rechtsableitungen

## 3.2 Top-Down-Analyse

### 3.2.1 Das Prinzip der Top-Down-Analyse

Blattfolge des bisher erzeugten Ableitungsbaums wird mit der Eingabesymbolfolge verglichen.

1. Beide Folgen enthalten gleiches Terminalsymbol: weiterlesen
2. Eingabefolge enthält Terminalsymbol und entsprechendes Blatt des Baumes Nichtterminalsymbol: Produktion der Grammatik auswählen auf die das Nichtterminalsymbol anwendbar ist
3. Zwei nicht übereinstimmende Terminalsymbole: vorher ausgewählte Produktion falsch oder Syntaxfehler in der Eingabe

**Probleme bei Top-Down-Analyse**

1. linksrekursive Produktionen
2. Verlaufen in Sackgassen (Lösbar durch *vorausschauende Syntaxanalyse*)

### 3.2.2 LL(k)-Grammatiken

LL(k) bedeutet

    Lesen von **l**inks nach rechts, Berechnen einer **L**inksableitung unter Vorausschau auf die nächsten k Zeichen.

**Begriffe:** FIRST-Menge, FOLLOW-Menge, Steuermenge

### 3.2.3 Berechnung von FIRST- und FOLLOW-Mengen, Modifikation von Grammatiken

FIRST- und FOLLOW-Mengen sind entscheidende Konstrukte bei der Realisierung von Top-Down-Analysen ohne Backtracking.

**Links-Faktorisierung**

Problem: Produktionen die auf der rechten Seite ein gemeinsames Präfix haben:

    A --> alpha beta_1 | alpha beta_2

Lösung: Produktion erzugen die das gemeinsame Präfix auswählt und Entscheidung "verschieben".

    A --> alpha A'
    A'--> beta_1 | beta_2

Die Technik kann auf beliebig viele Alternativen erweitert werden.

TODO: Algorithmus für FIRST-Menge beschreiben

TODO: Algorithmus für FOLLOW-Mengen beschreiben

### 3.2.4 Implementierung eines vorgreifenden Analysators mit Analysetabellen

TODO

### 3.2.5 Implementierung eines vorgreifenden Analysators durch rekursiven Abstieg

TODO
