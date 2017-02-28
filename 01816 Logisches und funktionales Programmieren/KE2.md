## 1.5 Nichtlogische Komponenten von Prolog
Darunter werden Eigenschaften von Prolog verstanden, die von der Prädikatenlogik abweichen beziehungsweise damit nicht beschreibbar sind.

Beispiele: Backtracking, Arithmetik, Ein- /Ausgabefunktionen, Cut-Operator, Negationen, ...

### 1.5.1 Suchraum eingrenzen mit "cut"-Operator !
Jeder Beweisschritt erzeugt einen Backtracking-Punkt auf dem Stack. Dies kann den Stack unter Umständen zum Überlaufen bringen. Mit dem Cut-Operator "!" kann der Bereich in dem nach Lösungen gesucht wird herausgeschnitten werden.

Der Programmierer ist dafür verantwortlich, dass nicht der Teil mit der potentiellen Lösung entfernt wird.

Der Operator steht anstelle eines Literals in der Anfrage oder auf der rechten Seite von Regeln. Rein logisch ist er **immer beweisbar**, beeinflusst jedoch das Verhalten des Backtrackingalgorithmus.

Gründe für die Anwendung des Cut-Operators:

1. Programmierer weiß bereits, dass bestimmte Alternativen in eine Sackgasse führen.  
2. Ein bestimmtes zu beweisendes Prädikat hat nur eine Lösung.  
3. Verhinderung von Laufzeitfehlern.  

**Beispiel** für die Anwendung:

> p :- q, !, r

Zunächst wird immer versucht *q* zu beweisen:

1. **q kann nicht bewiesen werden:** Es wird versucht die nächste Klausel ausprobiert (*r*). Der Cut-Operator hat keine Wirkung.

2. **q kann bewiesen werden:** *p* ist in diesem Fall nur beweisbar, wenn *r* beweisbar ist. Es wird die Variablenbindung von *q* genutzt. Fehlt das Beweisen von *r* fehl, wird keine Alternative geprüft.

> Alle alternative Beweismöglichkeiten für *p* die vor dem ! noch vorhanden waren werden abgeschnitten.

### 1.5.2 Negation
In  Prolog existiert das einstellige Prädikat "not" **\\+**, welches als Präfixoperator definiert ist. Bei dem Literal **\\+ X** wird zunächst versucht **X** zu beweisen. Ist dies beweisbar, ist **\\+ X** nicht beweisbar, anderfalls ist **\\+ X** beweisbar.

Die in Prolog verwendete Negation stimmt nicht mit der zugundeliegenden Logik überein. An einer Lösung wird gearbeitet. Die Idee ist es Negationen solange zu verzögern, bis alle vorkommenden Variablen gebunden sind.

###1.5.3 Zyklische Terme
Bei der Unifikation muss geprüft werden ob eine Variable als Variable im anderen Term vorkommt (**Vorkommenstest**). Aus Performancegründen wird hierauf oft verzichtet.

Die Bindung einer Variablen an einen Term wird häufig ein Zeiger realisiert der auf den Term zeigt. Ohne Vorkommenstest kann dies dazu führen, dass die Variable X auf einen zyklischen Term zeigt und es können Endlosschleifen entstehen.

###1.5.4 Arithmetik
Prolog bietet das zweistellige Infixprädikat **is**. X is Y ist beweisbar, wenn Y ein vollständig instantiierter arithmetischer Term ist und mit X unifizierbar. *2 + 3 is 2 + 3* ist  nicht unifizierbar, da zunächst das zweite Argument ausgerechnet wird und *2 + 3* nicht mit *5* unifizierbar ist.

Gründe, warum **is** nicht rein logisch ist:

1. partielles Prädikat, das heißt nicht jeder Term darf verwendet werden (zweites Argument muss vollständig instantiiert sein

2. Reihenfolge der Literale ist zu beachten

Prädikate, die **Vergleichen arithmetischer Werte**:

1. X =:= Y

2. X =\= Y

3. X < Y

4. X > Y

5. X >= Y

6. X =< Y

### 1.5.5 Ein- und Ausgabe
Ausnutzen von **Seiteneffekten**, also Operationen, die beim Beweisen "nebenbei" erfolgen und beim Backtracking nicht rückgängig gemacht werden.

**Eingabe von Daten** mit dem Prädikat *read* und in der Regel einer ungebundenen Variable. Beispiel: *read(X).* Die Eingabe muss ein gültiger Term sein (also auch mit einem Punkt abgeschlossen werden).

**Ausgabe von Daten** mit dem einstelligen Prädikat *write*. Dieses Prädikat ist genau einmal beweisbar. Seiteneffekt ist die Ausgabe des angegebenen Terms. Bei Ausgabe von Termen kann *writeq* genutzt werden, da dieses Prädikat die Anfürungszeichen nicht weglässt.

### Definieren eigener Operatoren
TO BE DONE

### 1.5.6 Dateien
Es gibt während eines Beweises immer genau eine Eingabe- und eine Ausgabedatei. Prädikate zur Eingabe lesen immer von der aktuellen Eingabedatei und Prädikate zur Ausgabe schreiben immer in die aktuelle Ausgabedatei.

Standardmäßig ist die aktuelle Eingabedatei die Tastatur, die aktuelle Ausgabedatei der Bildschirm. Der Dateiname **user** bezeichnet immer die Standardeingabe / -ausgabe.

**Prädikate für die Eingabe:** see(D), seeing(D), seen(D)

**Prädikate für die Ausgabe:** tell(D), telling(D), told(D)

**weitere Prädikate:** consult(D), reconsult(D), [D1, ..., Dn]

### 1.5.7 beliebige Termstrukturen
In den bisherigen Beispielen funktionierten Prädikate nur mit einer bestimmten Klasse von Termen (z.B. Listen), da die Klauseln explizit auf die Funktoren Bezug nahmen.

**Wichtigstes Prädikat** für die Arbeit mit beliebigen Termstrukturen ist *=..*

Es können Terme *zerlegt* werden, wenn das erste Argument mit diesen Termen instatiiert ist. Es können neue Terme *zusammengesetzt* werden, wenn das zweite Argument eine Liste mit dem Funktor und den Strukturkomponenten ist.

**functor(T, F, N)** wirkt wie =.. beachtet jedoch die Komponenten des Terms nicht

**arg(N, T, A)** dient dem Zugriff auf bestimmte Komponenten einer Struktur

**name(A, L)** zerlegt ein Atom in eine Liste seiner Buchstaben (als ASCII-Code)

**var(X)** ist beweisbar wenn X eine nicht instantiierte Variable ist

**nonvar(X)** Gegenteil von *var(X)*

**atom(X)** beweisbar wenn X ein Atom ist

**integer(X)** beweisbar wenn X mit einer ganzen Zahl instantiiert ist

**atomic(X)** Vereinigung von *atom(X)* und *integer(X)*

### 1.5.8 Erweiterte Anfragen
**call(X)** interpretiert beliebige Terme als Anfragen, es können nun Variablen für beliebige Terme stehen --> *Prädikatenlogik 2. Stufe* (Quantifizierung über Prädikate)

**true** ist immer genau einmal beweisbar

**fail** ist nie beweisbar

**\+X** ist beweisbar wenn *X* nicht beweisbar ist

**!** *cut*-Operator beeinflusst Backtracking-Verhalten

**repeat** ist beliebig oft beweisbar, beispielsweise zum Einlesen von Dateien

**X, Y** ist beweisbar wenn X *und* Y beweisbar sind --> logische UND-Verknüpfung

**X; Y** ist beweisbar wenn X *oder* Y beweisbar sind --> logische ODER-Verknüpfung

### 1.5.9 Veränderung der Datenbank
Syntaktische Struktur von Daten (Termen) und Programmen (Literalen, Klauseln) ist äquivalent. Daten Können als Programme intepretiert werden (mit *call*) und Programme als Daten. Oberbegriff *Datenbankprädikate* (wirken über Seiteneffekte).

**asserta/1:** Einfügen von Klauseln an den Anfang

**assertz/1:** wie oben, jedoch wird Klausel an das Ende angehangen

**retract/1:** Literal aus Datenbank löschen

**abolish/1:**

**clause/2:** Heraussuchen bestimmter Klauseln aus der Datenbank, wird häufig zum Programmieren von *Meta-Interpretern* genutzt

## 1.6 Praktisches Programmieren mit Prolog

### 1.6.1 Lösen von Denksportaufgaben

### 1.6.2 Programmierung von Meta-Interpretern
*Allgemein:* Ein Programm das in der Sprache P geschrieben wurde und beliebige Programme der Sprache P interpretieren (ausführen) kann. In funktionalen und logischen Programmiersprachen ist dies sehr einfach zu realisieren.

*Lemma-Generierung* ist das Hinzufügen bereits bewiesener Literale zum aktuellen Programm.

## 1.7 Neuere Entwicklungen

 - Verbesserung der Negation
 - Entwicklung paralleler logischer Programmierprachen
 - Modulkonzepte
 - Typkonzepte
 - Integration mit anderen Sprachen
 