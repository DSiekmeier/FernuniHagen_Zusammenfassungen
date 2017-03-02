# 2 Funktionale Programmierung
## 2.1 Einleitung
Funktionale Programme sind fast immer *kürzer*, *abstrakter* und besser *versteh- und modifizierbar* als imperative Programme

Funktionale Programme sind *inhärent paralell* also gut geeignet für die Ausführung auf hochparallelen Hardware-Strukturen. Charakteristisch ist außerdem, dass jeder Ausdruck einen *Rückgabewert* liefert.

Skript basiert auf Lisp-Dialekt *Scheme*. Dieser beinhaltet einen kleinen, funktionalen Kern ist jedoch relativ alt.

## 2.2 Der LISP-Dialekt *Scheme*
### 2.2.1 Elementare Sprachkonzepte
Lisp-Interpreter arbeitet mit der Schleife *Lesen-Auswerten-Schreiben* (**REPL**: read-eval-print-loop). Im interaktiven Modus werden Ausdrücke, in denen tatsächlich etwas berechnet wird durch einschließende, runde Klammern gekennzeichnet: *(+ 1 3)* (**Klammerausdrücke**). Elementare Datentypen werden einfach zurückgegeben.

**elementare Datentypen:** Zeichenketten (String), Zahlen (ganz oder Fließkomma), Symbole

**Auswertung eines Klammerausrucks**

>Erster Ausdruck (Operator) ist Funktion, die restlichen Ausdrücke sind Operanden. Klammerausdruck (+ 1 3) besteht also aus Operator + und Operanden 1 und 3. Interpretation als f(x, y) mit f = +, x = 1 und y = 2. Ausdrücke sind immer in **Präfix-Notation**

>**Genauer:** Zahlen und Zeichenketten werden vom Interpreter unverändert zurückgeliefert. Bei Symbolen werden die an sie gebundenen Werte zurückgegeben. Bei Applikationen werden alle in den Klammern enthaltenen Ausdrücke ausgewertet. Der Wert des Operators (muss Funktion sein) wird dann auf die Operanden angewendet. 

Hier: eine **Applikation** ist ein *echter* Funktionsaufruf in Abgrenzung an einen Klammerausdruck.

*Zeilen-Kommentare* werden durch ein Semikolon eingeleitet: ;

### 2.2.2 Symbole
Symbole sind Namen für "Gegenstände des Scheme-Universums" wie Variablen, Funktionsnamen, ... Symbole sind Zeichenreihen die bestimmte Sonderzeichen nicht enthalten, wie " , ; . und so weiter. Es wird nicht zwischen Groß- und Kleinschreibung unterschieden (üblich ist Kleinschreibung).

**Definieren von Symbolen:** (define pi 3.14)

Symbole können wieder ein Symbol als Wert haben. Dazu muss das Auswerten eines Ausdrucks verhindert werden (**Quotierung**): *(define sym-a 'sym-b)* oder *(define sym-a (quote sym-b))*

**Elementare Syntax**

Symbole, Zeichenketten, Zahlen und boolesche Konstanten **#t** und **#f** bezeichnet man als *Atome*.

### 2.2.3 Funktionsobjekte
Beispiel mit **Lambda-Ausdruck** (Indiana-Style):
	
	(define dbl (lambda (x) (+ x x) ) )

Der innere Ausdruck *(lambda (x) (+ x x))* erzeugt ein Funktionsobjekt (#procedure) und wird anschließend an das Symbol *dbl* gebunden. Die Definition lässt sich **verkürzt** schreiben (MIT-Style):

	(define (dbl x) (+ x x) )

Beide Schreibweisen sind semantisch völlig gleichwertig. Überall wo eine Funktion gebraucht wird, kann auch ein Lambda-Ausdruck stehen.

**Verschachtelte Applikationen** werden von innen nach außen ausgewertet. Dies nennt sich *eager evaluation*, *innermost evaluation* oder *applicative-order evaluation*. Wenn ein Parameterausdruck nicht terminiert kann auch die Applikation nicht terminieren. Dennoch ist eine **verzögerte Auswertung** möglich (*lazy evaluation*).

### 2.2.4 Prädikate und bedingte Ausdrücke
**Prädikate** haben einen boolschen Rückgabewert: <, >, =, <=, >=, or, and, not.

Zur **Fallunterscheidung** dienen die Funktionen *cond* und *if*. Bei **cond** wird eine Reihe von Prädikaten untersucht, bis eines nicht zu **#f** auswertet. Ist dies bei keinem der Fall ist **cond** undefiniert, außer es existiert ein **else**-Ausdruck.

**if** entspricht einem **cond** mit lediglich einer Bedingung und dem **else**-Zweig.

**Makros** (*special forms*) sind Klammerausdrücke die nicht wie üblich ausgewertet werden. Dazu gehören: define, quote, lambda, if, cond, and und or sowie let, set!, delay und cons-stream.

### 2.2.5 Programmstuktur

### 2.2.6 Umgebungen
