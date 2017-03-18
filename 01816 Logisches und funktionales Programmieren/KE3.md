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

## 2.3 Funktionale Abstraktion
Einteilung des Programms in überschaubare Einheiten (Module). Hervorgehoben werden hier die beiden Aspekte

1. Unterscheidung zwischen Funktionsdefinitionen und den Rechenprozessen die sie erzeugen und
2. Verwendung von Funktionen als Parameter und / oder Ergebnis von Funktionen

### 2.3.1 Rekursive und iterative Prozesse
- Höchstens ein nicht abgeschlossener Rechenschritt: **linear rekursiver Rechenprozess** (linearer Speicherverbrauch)
- durch Hinzufügen eines Hilfskonstrukts kann daraus auch ein iterativer Prozess entstehen

> Eine rekursive Funktionsdefinition kann sehr wohl einen iterativen Rechenprozess definieren. **Endständig rekursive Funktionen**

Spezielle Konstrukte wie *while* oder *for* wie in imperativen Sprachen sind in Scheme nicht notwendig.

Erzeugt ein Funktionsaufruf mehr als eine Rekursion spricht man von **baumrekursiven Prozessen** oder **Baumrekursion** (Standard-Beispiel *Fibonacci-Zahlen*). Speicherbedarf ist dann proportional zur Tiefe des Rekursionsbaums. Zeitverbrauch proportional zur Anzahl der Knoten im Baum.

### 2.3.2 Funktionen höherer Ordnung
**Funktionen höherer Ordnung** sind Funktionen, die Funktionen als Argumente oder Ergebnisse haben. Komplexe Programme können aus wenigen primitiven Elementen erstellt werden.

### 2.3.3 Funktionen als Parameter von Funktionen
Beim Aufruf einer Applikation mit Funktionen als Parameter werden diese nicht sofort ausgeführt sondern liefern bei der Ausführung lediglich die an sie gebundenen Objekte als Symbol. **(siehe Abschnitt 2.2.8)**

**let-Makro** dient dem Definieren lokaler Namen mit Einschränkung der Sichtbarkeit auf Teile eines Prozedurrumpfes.

### 2.3.4 Funktionen als Ergebnisse von Funktionen
Wesentliches Merkmal einer funktionalen Sprache, dass eine **Funktion als Ergebnis einer Applikation** auftreten kann.

In Scheme und Ähnlichem sind Funktionen völlig gleichberechtigt mit anderen Datentypen wie Zahlen, Zeichenketten und so weiter.

Funktionen höherer Ordnung enthalten nicht nur Berechnungsanweisungen sondern auch *Informationen über die zum Zeitpunkt ihrer Entstehung existierenden Parameterbindungen*.

**Sequentielle Dekomposition** für das Lösen komplexer Probleme: Problem eine Funktion zu definieren wird zurückgeführt auf das Definieren zweier einfacherer Funktionen. Ist *f Komposition von g und h* kann f definiert werden durch

	( define ( f x ) ( g ( h( x ) ) )

Abstrahiertes Beispiel: *compose* hat zwei Funktionen als Argumente und gibt eine Funktion als Ergebnis zurück.

	( define ( compose g h ) ( lambda (x) ( g ( h( x ) ) ) ) )

## 2.4 Datenstrukturen und Datenabstraktion
**cons**: Elementare Funktion zum Erstellen zusammengesetzter Objekte. Die zweikomponentige Datenstruktur wird auch *dotted-pair* genannt.
	
	( cons 1 2 ) -> ( 1 . 2 )

Verschachteln mehrerer **cons**-Aufrufe führt zu einer beliebig komplexen Baumstruktur.

	( cons ( cons 1 2 ) 3 ) -> ( ( 1 . 2 ) . 3 )

Im Gegensatz zu **dottet-pairs** haben **Listen** immer eine leere Liste () als rechtes Blatt.

**list** ist die Standardoperation zur Erstellung von Listen fester Länge.

	( cons 1 ( cons 2 ( cons 3  '() ) ) ) == ( list 1 2 3 ) == ( 1 2 3)

Es gibt eine **syntaktische Ähnlichkeit** zwischen Programmen und Daten. Alle Ausdrücke sind zunächst Daten. Programme sind nach zusätzlichen Kriterien aufgebaute Ausdrücke (ähnlich wie bei Prolog). Ähnlichkeit zwischen Daten und Programmen ist charakteristisch für KI-Sprachen.

Funktionen zum **Zugreifen auf Komponenten** einer Liste sind *car* und *cdr*. *car* liefert das erste Element einer Liste. *cdr* liefert wieder eine Liste bestehend aus dem Rest (ohne erstes Element). **null?** dient zum Testen auf leere Listen.

Weitere **Operationen auf Listen**: atom?, number?, symbol?, string?, boolean?

**i-tes Element einer Liste**

	( define ( ith i li )
		( if ( = i 0 ) ( car li ) ( ith ( - i 1 ) ( cdr li))))

**Längenabfrage**

	( define ( len li )
		( if ( null? li ) 0 ( + 1 ( len ( cdr li )))))

**Konkatenation**

	( define ( app li r )
		( if ( null? li ) r ( cons ( car li ) ( app ( cdr li ) r ))))

Keine der Funktionen ändert das Argument. Es wird eine Kopie erzeugt und zurückgegeben. **Nachteil:** großer Speicherbedarf und lange Laufzeiten. **Vorteil:** Sicherheit da es keine Nebeneffekte gibt. Im Hintergrund arbeitet **Garbage Collector**.

**Bäume / Binärbäume**
Standardrekursionsstruktur für Programme mit Bäumen ist ein *cond* mit drei Zweigen: *null?* zum Abfangen leerer Listen, *atom?* für Bäume mit nur einem Knoten und *else* in dem mit car und cdr zwei Teilbäume selektiert werden.

**Syntaxbäume**
sind ein Anwendungfall von *markierten Bäumen* also Bäumen, die auch Informationen in den inneren Blättern führen.

### 2.4.2 Generische Programmpakete
**Datenabstraktion** ist wesentliches Prinzip für die Entwicklung von flexiblen und zuverlässigen Programmen. Die konkrete Repäsentation von Daten wird verborgen und der Nutzer sieht nur die logischen Operationen darauf. Teilaspekt in Scheme ist das Erstellen *generischer Softwarepakete*. Dabei kommt zum Beispiel das *Überladen* von Operatoren zum Einsatz.

**1- Datengerichtete Prgrammierung**
Beim Überladen von Operatoren ist eine *Instanz* notwendig die je nach Datentyp festlegt, wie die Funktion ausgefürt werden soll. Möglichkeit: Die Funktion selber übernimmt die ganze Arbeit.

In Scheme müssen auch zur Laufzeit die Datentypen bekannt sein (nicht wie bei kompilierten Sprachen). Möglichkeit: stets Paare aus Datum und Typinformation verwalten.

> Datengerichtete Programmierung ist die logische Fortsetzung dieses Konzepts. Daten werden mit ihren Typen *ettiketiert*.

Ansatz, dass Funktion alles übernimmt ist **nicht** sehr elegant und sicher, da bei neuen Datentypen vieles angepasst werden muss. Besser: Funktionen wie Daten behandeln und in einer Tabelle ablegen. Dabei dreidimensionale, zentrale Tabelle für Operatoren und Typ des Ergebnisses.

**Vorteil:** Es muss nur die Operatortabelle geändert werden und nicht die Funktionen, solange diese die Daten korrekt ettiketieren.
**Nachteil:** Sicherheit geht zugunsten der Flexibilität verloren, da keine statische Typprüfung erfolgen kann. Viele Kritiker von Scheme halten diesen Nachteil für zu groß. Moderne Sprachen wie Haskell haben Typsicherheit und Flexibilität.
