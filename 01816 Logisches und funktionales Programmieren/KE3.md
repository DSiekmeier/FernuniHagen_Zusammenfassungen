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
Umgebungen bestimmen den **Sichtbarkeits- und Gültigkeitsbereich** von Variablen. Sichtbarkeitsregeln entsprechen den *Scope*-Regeln wie in Pascal: Deklarationen sind im gesamten direkt umfassenden Block un den inneren Blöcken sichtbar, sofern hier keine Redefinition stattfindet.

Sichtbarkeitsbereiche sind unabhängig von der Aufrufreihenfolge der Funktionen.

**statische Bindung**: Die Sichtbarkeit eines Symbols kann direkt aus dem Quellcode abgelesen werden.

**Grundbegriffe**

**1. Rahmen (*engl. frame*):** Ein Rahmen r ist eine Tabelle von Bindungen, die Symbolen je genau einen Wert zuordnet.

**2. Umgebung (*engl. environment*):** Eine Umgebung U ist eine durch *Verweise* verkette Liste von Rahmen. Schreibweise: U = (r_1, ..., r_n) oder U = (r_1 . U')

**3. Umgebungsspeicher:** Enthält alle Umgebungen, insbesondere die *globale Umgebung*

Zu Beginn existiert lediglich der Rahmen der globalen Umgebung. Neue Rahmen werden bei einem Funktionsaufruf (benutzerdefinierte Funktionen) erzeugt. Der neue Rahmen verweist auf seinen statischen Vorgänger (Definitionsumgebung).

Ein *define* auf Intepreterebene erzeugt zunächst einen Neueintrag in der globalen Umgebung. Lokale Definitionen einer Funktion werden in einem neuen Rahmen an die Parameter gebunden.

### 2.2.7 Abschlussobjekte
Schlüsselbegriff der funktionalen Programmierung (*engl. closure*).

Bei der Definition eines Funktionsobjekts wird das Bindungspaar **Symbol**, **Lambda-Ausdruck** (Berechnungsanweisung) und ein **Verweis auf Definitionsumgebung** angelegt.

Das Paar **lambda-Ausdruck** und **Umgebung** heißt **Abschlussobjekt**. Die Funktion "merkt sich" in welchen Kontext sie entstanden ist.

### 2.2.8 Auswertungsregeln
Regeln für die Auswertung eines Ausdrucks e in der Umgebung U:

**1. Konstanten:** > Ist e eine Zahl, Boolscher Wert oder Zeichen(kette) wird e selbst zurückgegeben

**2. Symbole:** > Ist e ein Symbol x wird in der Umgebung U = (r_1 ... r_n) nach der Bindung x:v gesucht und v zurückgegeben. Ist x ungebunden endet die Auswertung mit einem Fehler.

**3. Applikationen:** Ist e=(e_0 ... e_n) werden erst in beliebieger Reihenfolge die e_i ausgewertet was Werte v_i ergibt. v_0 muss n-stellige Funktion sein. TODO

**4. Definitionen:** TODO

**5. lambda-Ausdrücke:** TODO

**6. Sequenzen von Ausdrücken:** TODO

**7. Makros:** Auswertung nach speziellen Regeln der Makros.

- Folgen von Defininitionen werden sequentiell ausgewertet
- Unproblematisch sind Funktionsdefinitionen in denen erst später definierte Funktionen aufgerufen werden
- Umgebungen sind Listen, die gemeinsame Vorgänger haben: in einer Umgebung können sich während der Abarbeitung Bindungen ändern aber die Identität der Umgebung wird gewahrt.
- für rein funktionales Scheme existiert das Subsitutionsmodell für die Ausdrucksauswertung (statt Umgebungsmodell)

