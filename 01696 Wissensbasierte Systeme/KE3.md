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
