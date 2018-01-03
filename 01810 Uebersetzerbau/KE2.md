# 3 Syntaxanalyse
Syntaxanalyse ist zweite Phase der Übersetzung mit dem Ziel aus der Tokenfolge vom Scanner einen Syntaxbaum (auch Ableitungsbaum) zu erstellen. Basis ist die *Grammatik* die die Syntax der Quellsprache beschreibt.

Es werden zwei Vorgehen unterschieden:

**1. Top-Down-Analyse:** Der Baum wird von der Wurzel aus aufgebaut, beginnend vom Startsymbol der Grammatik.

**2. Bottom-Up-Analyse:** Der Baum wird von den Blättern her aufgebaut indem solange Token eingelesen werden, bis eine vollständige rechte Seite der Grammatik vorliegt.