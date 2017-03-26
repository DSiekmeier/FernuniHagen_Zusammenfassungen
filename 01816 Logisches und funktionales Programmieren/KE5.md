# 3 Logisches Programmieren mit Constraints
## 3.1 Einleitung und Motivation
## 3.2 Bedingungsüberprüfung in Prolog
### 3.2.1 Generate-and-test
**Generate-and-test** ermöglicht elegantes Lösen vieler Suchprobleme. Schema dieser Vorgehensweise ist wie folgt:
	
	loesung( L ) :- potentielleLoesungen( L ), korrekteLoesung( L ).

Das erste Literal *generiert* zunächst nach und nach alle potentiellen Lösungen und "übergibt" diese an das zweite Literal. Dieses *testet* deren Korrektheit.

**Beispiel:** N-Damen-Problem

### 3.2.2 Standard-Backtracking
Generate-and-test-Algorithmen häufig sehr ineffizient. Idee: Phasen des Generierens und Testens stärker miteinander verzahnen. Beim N-Damen-Problem: sofort nach dem Platzieren einer Dame die Kompatibilität zu bereits gesetzten Figuren prüfen.

**Problem 1:** Viele Backtrackingschritte bei großen N notwendig.

**Problem 2:** Verzahnen der Phasen bei vielen Problemen sehr komplex.

### 3.2.3 Forward-Checking
Nach dem Auswählen wird die Wertemenge der verbleibenden Variablen eingeschränkt. Hoher Verwaltungsaufwand notwendig. Programmieraufwand ist höher und Modifikation des Programms aufwendiger. Für kleine N ist Standard-Backtracking effizienter.

**Standard-Backtracking:** Prüfung der einschränkenden Bedingungen *nachher* -- passive Bedingungen
**Forward-Checking:** Prüfung der einschränkenden Bedingungen *vorher* -- aktive Bedingungen

## 3.3 Das Constraint-Lösungskonzept
Verwaltung und Überprüfung von Bedingungen werden nicht explizit durch das Programm sondern automatisch durch das (Scheme-)System erfolgen.

### 3.3.1 Überblick
Entscheidende Idee bei der constraint-logischen Programmierung: Erweiterung des Berechnungsbereichs (z.B. durch Zahlenarithmetik).

**Idee:** Erweiterung der Unifikationsprozedur (in manchen Fällen nicht möglich). Es existieren Vorschläge für folgende Bereiche:

**1. Lineare arithmetische Terme:**
**2. Boolsche Terme:**
**3. Terme über endlichen Bereichen (Finite Domains):**

### 3.3.2 Constraints
**Constraints:** Sprackkonstrukte, die Bedingungen oder Einschränkungen an die Bindung von Variablen ausdrücken. Diese werden vom System zur Laufzeit geprüft und berücksichtigt.

### 3.3.3 Verallgemeinerter Antwortbegriff
Um neben Gleichheitsconstraints auch allgemeinere Constraints behandeln zu können, wird ein allgemeineres Lösungsverfahren benötigt.

Bestimmte Systeme (Prolog-III, CLP(R)) können lineare Gleichungen lösen um Anfragen wie folgende zu lösen (sollte 5 liefern):

	p( X, Y ) :- X >= 5, Y <= 5.
	p( Z, Z ).

### 3.3.4 Unifikation, Resolution und Constraint-Solving
Verbindung von Unifikation und Constraint-Lösen auf zwei Arten möglich:

1. Unifikation wie üblich, jedoch wird bei Auftauchen von Constraint-Variablen der Constraint-Solver aufgerufen. Entspricht *Resolution + Unifikation + Constraint-Solving*
2. Unifikation eingebettet in Constraint-Solver. Unifikation wird also nicht anders als Constrain betrachetet. Entspricht *Resolution + Constraint-Solving* mit *Unifikation Teilmenge von Constraint-Solving*

## 3.4 Constraint-logische Programmierung mit endlichen Bereichen
*Vereinbarung:* "CLP(FD)-Programme" wird mit "CLP-Programme* abgekürzt (also Betrachtung nur über endlichen Bereich, Finite Domains).

### 3.4.1 Endliche Bereiche und Domainvariablen
Berechnungen in CLP erfolgen über

1. endlichen Bereichen (nicht-leere Menge von Konstanten; B ist i.F. eine Menge endlicher Bereiche)
2. Herbrand-Universum (Menger der bildbaren Grundterme)

**Domainvariablen** sind für jeden Bereich *d* in *B* vorhanden, Bezeichnung x^d, y^d, ...
**einfache Variablen** sind keine Domainvariablen
**Variablen** sind Domainvariablen und einfache Variablen

Terme, Klauseln, Anfragen etc. bleiben gleich. Lediglich der Variablenbegriff wird erweitert.

### 3.4.2 Unifikation mit Domainvariablen
Der Begriff der Unifikation wird erweitert: Eine Domainvariable kann nur an ein Element aus *d* gebunden werden oder an eine Domainvariable deren Bereich in *d* enthalten ist.

> Begriffe für den Umgang mit der Unifikation verallgemeinern sich auf Domainvariablen. Auch Existenz eines allgemeinsten Unifikators ist gegeben.

**Algorithmus zur Berechnung des allg. Unifikators mit Domainvariablen**
Drei Fälle sind zu unterscheiden:

**1. Domainvariable und Konstante:** Konstante muss im Bereich der Domainvariablen liegen
**2. Domainvariable mit einfacher Variable:** einf. Variable wird mit Domainvariable gebunden
**3. zwei Domainvariablen:** neue Domainvariable mit Bereich = Durchschnitt der anderen

### 3.4.3 Inferenzregeln
Prinzip der Resolution kann auf constraint-logische Programmierung übertragen werden. Normale Termunifikation wird durch erweiterte (mit Domainvariablen) ersetzt.

Daneben gibt es spezielle Inferenzregeln.

#### 3.4.3.1 Forward Checking in CLP
Constraints in denen es nur noch **eine nicht-instantiierte Variable** gibt, dazu verwendet werden den Bereich der letzten Variablen einzuschränken.

> Ein n-stelliges Constraint p ist **vorwärts-überprüfbar**, falls genau eines der Argumente eine Domainvariable ist und alle anderen Grundterme. Die Domainvariable heißt dann **Vorwärts-Variable**.

**Definition: Forward-Checking-Inferenzregel (FCIR)** TODO

#### 3.4.4.2 Looking Ahead in CLP
Auch anwendbar, wenn es in dem Constraint noch **mehr als eine Variable** gibt. Idee: Aus dem Wertebereich jeder Variablen die Werte entfernen zu denen es keine konsistente Belegung der übrigen Variablen gibt.

**Definition Look Ahead-Regel (LAIR)** TODO

**Vergleich von FCIR und LAIR mit allgemeiner Resolutionsregel**

1. LAIR weniger restriktiv, da es mehr als eine Variable geben darf
2. Bereiche der Domainvariablen werden eingeschränkt und Var. instantiiert wenn nur noch ein Wert übrig ist
3. TODO

### 3.4.4 FD-spezifische Prädikate
Es gibt keinen allgemein akzeptierten Standard. Implementierungen haben oft unterschiedliche **Aufrufmuster**.

#### 3.4.4.1 Spezifikation endlicher Bereiche
**domain** p( d1, ..., dn ) definiert Domain-Deklaration
**fd_min( ?X, ?N )** unifiziert für X den minimalen Wert den X aktuell annehmen kann mit N
**fd_max( ?X, ?N )** wie fd_min
**fd_size( ?X, ?N )** unifiziert die Kardinalität 

#### 3.4.4.2 Arithmetische Constraints

#### 3.4.4.3 Auswahlprädikate

#### 3.4.4.4 Symbolische Constraints

## 3.5 CLP-Programmiertechniken und Anwendungsbeispiele
### 3.5.1 Forward-Checking
Forward-Checking kann mit Constraints sehr viel einfacher formuliert werden.

**Standard-Backtracking** hat folgende Nachteile:

1. Wiederholtes Auffinden desselben Sachverhalts
2. Spätes Auffinden von Fehlern und nuztloses Generieren von Werten
3. Ungeschickter Rücksetzpunkt

### 3.5.2 Verallgemeinerstes Forward-Checking
Zugrundeliegendes Schema **constrain-and-generate**.

### 3.5.3 Constrain-and-generate
Dies ist eine grundlegende CLP-Programmiertechnik. Typische Anwendungsfälle für constraint-logische Programmierung: kombinatorische Probleme, Produktionsplanung, ...

Es gibt zwei Punkte an denen man die Auswahl der Variablen steuern kann:

1. choose_decision_variable
2. choose_value

### 3.5.4 Das First-Fail-Prinzip
Geschickte Auswahl von Variablen kann das Forward-Checking oft noch verbessern:

**First-Fail-Prinzip:** Auswahl der Variablen mit dem kleinsten noch möglichen Wertebereich. Bei der also ein Scheitern zuerst zu erwarten ist.

## 3.6 Finite-Domain-Constraints in SICStus-Prolog
### 3.6.1 Einführung
Laden der FD-Constraint-Bibliothek mit
	
	use_module( library( clpfd) ).

### 3.6.2 FD-spezifische Prädikate
#### 3.6.2.1 Spezifikation endlicher Bereiche
#### 3.6.2.2 Arithmetische Constraints
Relationen die als Constraints benutzt werden sollen bekommen ein # vorangestellt.
#### 3.6.2.3 Auswahlprädikate
#### 3.6.2.4 Symbolische Constraints

## 3.7 CLP-Systeme im Überblick

1. CLP(R)
2. Prolog III
3.CHIP

# 4 Interation von logischen und funktionalen Programmieren
## 4.1 Motivation
Wesentliche Merkmale der **logischen Programmierung**

1. logische Variablen
2. partielle Datenstrukturen
3. eingebaute Suche

Wesentliche Merkmale der **funktionalen Programmierung**

1. verschachtelte Ausdrücke
2. Funktionen höherer Ordnung
3. verzögerte Auswertung (*lazy evaluation*)

Punkte, die für die **Kombination der beiden Paradigmen** sprechen:

1. Funktionen vs. Relationen: Funktionen sind nichts anderes als spezielle Relationen
2. Elemente höhrere Ornung: Logische Programmiersprachen sind auf Logik erster Stufe beschränkt, ist aber ein mächtiges Konzept bei funkt. Programmierung
3. Suche und Ablaufsteuerung: Bei log. Programmierung kann bei der Problemlösung auf Suchverfahren zurückgegriffen werden.
4. Parallele Datenstrukturen: 
5. Datenfluss: 
6. Implementierungstechniken:
7. Programmierkonzepte:

**Essentielle Unterschiede** zwischen den beiden Paradigmen:

1. Logische Variablen und Unifikation in Prolog
2. Nichtdeterminismus in Prolog
3. Möglichkeit von Funktionen und Relationen höherer Ordnung

**Ansätze**

1. Einschränkung des Gebrauchs log. Variablen (und somit Suchraums) um funktionales Verhalten zu erreichen
2. Erweiterung funktionaler Sprachen um logische Variablen

## 4.2 Kombination verschiedener Sprachen
Statt eine neue Sprache zu erfinden: Ansätze zur Kombination wie *LOGLISP*. Resultat ist sehr mächtig jedoch zwei wichtige Nachteile:

1. Eventuell Konvertierung von Datenstrukturen notwendig
2. Beide Sprachkonzepte bleiben voneinander getrennt (komplizierte Semantik)

## 4.3 Unifikationn und logische Variablen
- Einschränkung von logischen Variablen durch Angabe ob Argument im Prädikat Ein- oder Ausgabeposition ist
- Diese *mode*-Deklaration verhindert jedoch Awendung des Prädikats in "umgekehrter Richtung"
- Hat zur Auswirkung, dass keine volle Unifikation mehr notwendig ist
	- *eineitige Unifikation* oder *Pattern Matching* ist ausreichend bei Eingabeparametern
	- Ausgabeparameter werden an Ausgabevariablen gebunden
- Entspricht im Wesentlichen der musterorientierten Programmierung in der funkt. Programmierung. Vorteil: mit relationaler Schreibweise können einfach Funktionen mit Tupeln als Ergebnis definiert werden

## 4.4 Funktionales Programmieren und logische Variablen
Einführung logischer Variablen in die funktionale Programmierung. **Notation von Definitionsgleichungen** mit Parametermustern wie in Haskell. Der Kern einer funktionalen Sprache kann letzendlich immer auf Definitionsgleichungen zurückgeführt werden. Operationale Auswertung erfolgt duch entsprechende **Reduktionsschritte**.

**Eigenschaften von Definitionsgleichungen:**

**1. Konfluenz:**
**2. Terminierung:**

Für jedes System von Definitionsgleichungen die diese beiden Eigenschaften hat gilt, dass jeder Term *t* zu einem eindeutigen, nicht weiter reduzierbaren Term *t'* (*Normalform von t*) reduziert werden kann.

**Definition Narrowing:** 

Beispiel für Sprache mit Narrowing ist Eqlog. **Nachteil von Narrowing** ist die Komplexität des entstehenden Suchraums.

## 4.5 Funktional-logische Programmierung
Drei verschiedene Betrachtungsweisen um Paradigmen näher zu bringen:

1. Kombination der Sprachen
2. Einbringen funktionaler Aspekte in das logische Programmieren
3. Einbringen von Konzepten der logischen Programmierung in funktionale Sprachen

Aspekte die eine funktional-logische Programmiersprache auszeichnet:

1. Umfasst sowohl (reines) logisches als auch (reines) funktionales Programmieren, bietet also Möglichkeiten von verschachtelten Funktionsausdrücken, Funktionen höherer Ordnun, lazy evaluation, logische Variablen, ...
2. Bietet effizientere Auswertungsmechanismen als logische Sprachen da funktionale Ausdrücke deterministische ausgewertet werden (*cut*-Operator kann vermieden werden).
3. *call*-Prädikat zur Simulation von Funktionen höherer Ordnung kann vermieden werden.

Es gibt noch keinen anerkannten Standard für die Symantik aber zwei Ansätze:

**1. Residuation:** Funktionsaufrufe mit nicht vollständig vorliegenden Argumentenwerden so lange verzögern, bis die Aufrufe deterministisch ausgewertet werden können.

**2. Narrowing:**