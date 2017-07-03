# 4 Regelbasierte Systeme
## 4.1 Was sind Regeln?
Regeln sind *formalisierte Konditionalsätze* der Form

	Wenn (if) A dann (then) B.

Der "Wenn"-Teil wird *Prämisse* genannt, der "Dann"-Teil *Konklusion*. Gilt die Regel ohne Ausnahme spricht man von einer *deterministischen* Regel.

Regeln sind ein guter Kompromiss zwischen Verständlichkeit der Wissensdarstellung und formalen Ansprüchen.

Bei der Modellierung wird häufig wert auf eine *einfache syntaktische Form* gelegt.

1. Keine Disjunktion (Oder-Verknüpfung) in der Prämisse
2. Keine Konjunktion (Und-Verknüpfung) in der Konklusion

Dies vergrößert zwar die Anzahl der Regeln macht sie aber einfacher les- und verarbeitbar.

## 4.2 Die Wissensbasis eines regelbasierten Systems
Die Wissensbasis enthält *Objekte* und deren Beschreibungen mittels einer endlichen Menge diskreter Werte. *Regeln* repräsentieren Zusammenhänge zwischen den Objekten oder Objektmengen.

> Objekte und Regeln bilden das **abstrakte** Wissen der Wissensbasis. Bei Anwendung auf einen konkreten Fall kommt das **fallspezifische** Wissen hinzu (unmittelbare Beobachtungen und abgeleitetes Wissen).

## 4.3 Inferenz in regelbasierten Systemen
Grundlegende Inferenzregel ist der **modus ponens**:

	If A then B	(Regel)
	A wahr		(Faktum)
	---------------------------
	B wahr		(Schlussfolgerung)

Die Regel ist Teil des abstrakten Wissens, das Faktum ist Teil des fallspezifischen Wissens (da im Allgemeinen eine Beobachtung).

Der *modus ponens* benutzt jeweils eine Regel zur Inferenz. Eine *Verkettung von Regeln* ist möglich. Man unterscheidet zwischen **Vorwärtsverkettung** (datengetriebene Inferenz) und **Rückwärtsverkettung** (zielorientierte Inferenz).

### 4.3.1 Regelnetzwerke
**Regeln sind gerichtet**, das heißt, sie können nur dann feuern wenn ihre Prämisse erfüllt ist. Dies ist ein Unterschied zur klassischen Logik. Möchte man die "Kompatibilität" zur klassichen Logik, kann dies durch zusätzliche Anwendung des **modus tollens** erricht werden.

### 4.3.2 Datengetriebene Inferenz (Vorwärtsverkettung)
Regeln werden transitiv verknüpft, das bekannte fallspezifische Wissen dient als Ausgangspunkt für Schlussfokgerungen (daher *data-driven*). Konklusionen die aufgrund von erfüllten Prämissen "entstehen" dienen als abgeleitete Fakten und gehen als neues faktisches Wissen in die Wissensbasis ein. Der Algorithmus terminiert wenn keine neuen Fakten abgeleitet werden können.

Die Vorwärtsverkettung ist nützlich im einen Überblick über den Gesamtzustand des Systems zu bekommen.

### 4.3.3 Zielorientierte Inferenz (Rückwärtsverkettung)
Die Rückwärtsverkettung kann zur Informationsbeschaffung über bestimmte Knoten verwendet werden. Wieder werden Regeln transitiv verknüpft, Ausgangspunkt ist jedoch ein bestimmtes Zielobjekt über das Informationen beschafft werden sollen.

Das Inferenzsystem sucht nach Regeln, die das Zielobjekt als Konklusion haben. Die Objekte der Prämissen werden zu Zwischenzielen. Die Liste von Zielen wird abgebaut bis sie leer ist. Der Algorithmus ist als *BACKCHAIN* rekursiv realisiert.

## 4.4 Das Problem der Widersprüchlichkeit
Negationen in Fakten oder Konklusionen von Regeln können zu wiedersprüchlichen Aussagen führen.

1. Regelbasis kann klassisch-logisch inkonsistent sein
2. Regelbasis führt zu widersprüchlichen Aussagen

## 4.5 Die Erklärungskomponente
Die Erklärungskomponente dient dazu die Argumentationskette zu erläutern. Dazu werden zum Beispiel die zur Schlussfolgerung genutzten Regeln aufgelistet.

## 4.6 Signalsteuerung im Eisenbahnverkehr durch Regeln
TODO

## 4.7 MYCIN -- Ein verallgemeinertes regelbasiertes System
MYCIN beinhaltete bereits Verfahren zur Repräsentation und Verarbeitung *unsicheren Wissens*. Die Wissensrepräsentation erfolgtdurch **Regeln mit Sicherheitsfaktoren** (Zahl zwischen -1 und +1).

Die Inferenzkompontente von MYCIN arbeitet prinzipiell wie ein **rückwärtsverketteter Regelintepreter**. Als Ausgabe erfolgt jedoch nicht nur ob das Zielobjekt wahr oder falsch ist sondern auch ein Faktor für die Sicherheit des Objekts. Dazu werden die Sicherheitsfaktoren in geeigneter Weise miteinander verknüpft.

Die Erklärungskomponente von MYCIN hat ein *Question-Answering-Modul* welches Fragen über Zusammenhänge und die Schlussfolgerung beantwortet und ein *Reasoning status checker* der die aktuelle Argumentationskette transparent macht.

## 4.8 Modularität und Effizienz regelbasierter Systeme
Man erzielt volle Modularität indem in einem "idealen" System jede Regel als **Wissenseinheit** unabhängig vom Rest der Wissensbasis behandelt wird. Neues Wissen kann so einfach "angehängt" werden.

Das unstrukturierte Wissen kann jedoch zu Effizienz- und Suchproblemen führen, insbesondere da nicht zwangsläufig nur eine Regel sondern *alle* in Frage kommenden Regeln gesucht werden müssen.

Die Suche kann effizienter erfolgen indem Regeln nach Häufigkeit der Anwendung sortiert oder feste Prioritäten bei der Suche gesetzt oder die Regeln in Klassen eingeteilt werden die je nach Fragestellung durchsucht werden.

## 4.9 Ausblick
TODO
