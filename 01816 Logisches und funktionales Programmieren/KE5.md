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
Constraints in denen es nur noch eine nicht-instantiierte Variable gibt, dazu verwendet werden den Bereich der letzten Variablen einzuschränken.

> Ein n-stelliges Constraint p ist **vorwärts-überprüfbar**, falls genau eines der Argumente eine Domainvariable ist und alle anderen Grundterme. Die Domainvariable heißt dann **Vorwärts-Variable**.

**Definition: Forward-Checking-Inferenzregel (FCIR)**