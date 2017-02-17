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
