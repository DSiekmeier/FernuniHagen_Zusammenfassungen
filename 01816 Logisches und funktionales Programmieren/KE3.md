# 2 Funktionale Programmierung
## 2.1 Einleitung
Funktionale Programme sind fast immer *kürzer*, *abstrakter* und besser *versteh- und modifizierbar* als imperative Programme

Funktionale Programme sind *inhärent paralell* also gut geeignet für die Ausführung auf hochparallelen Hardware-Strukturen.

Skript basiert auf Lisp-Dialekt *Scheme*. Dieser beinhaltet einen kleinen, funktionalen Kern ist jedoch relativ alt.

## 2.2 Der LISP-Dialekt *Scheme*
### 2.2.1 Elementare Sprachkonzepte
Lisp-Interpreter arbeitet mit der Schleife *Lesen-Auswerten-Schreiben* (**REPL**: read-eval-print-loop). Im interaktiven Modus werden Ausdrücke, in denen tatsächlich etwas berechnet wird durch einschließende, runde Klammern gekennzeichnet: *(+ 1 3)* (**Klammerausdrücke**). Elementare Datentypen werden einfach zurückgegeben.

**elementare Datentypen:** Zeichenketten (String), Zahlen (ganz oder Fließkomma), Smybole

**Auswertung eines Klammerausrucks**

>Erster Ausdruck (Operator) ist Funktion, die restlichen Ausdrücke sind Operanden. Klammerausdruck (+ 1 3) besteht also aus Operator + und Operanden 1 und 3. Interpretation als f(x, y) mit f = +, x = 1 und y = 2. Ausdrücke sind immer in **Präfix-Notation**

Hier: eine **Applikation** ist ein *echter* Funktionsaufruf in Abgrenzung an einen Klammerausdruck.

*Zeilen-Kommentare* werden durch ein Semikolon eingeleitet: ;

### 2.2.2 Symbole