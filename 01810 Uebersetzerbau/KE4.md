# 4 Syntaxgesteuerte Übersetzung

Frage: Wie wird aus dem gegebenen Ableitungsbaum ein Programm der Zielsprache generiert?

In der Regel werden bereits Teilstrukturen des Baums übersetzt und nicht bis zur vollständigen Erstellung gewartet.

Formale Grundlage der *syntaxgesteuerten Übersetzung* sind *attributierte Grammatiken*. Verbinden Übersetzungsaktionen mit dem Erkennen von Teilstrukturen des Ableitungsbaums.

## 4.1 Attributierte Grammatik, syntaxgesteuerte Definition

Zentrales Problem ist die Assoziation von Informationen mit den Teilstrukturen des Ableitungsbaums

--> Jedes Symbol der Grammatik bekommt *Attribute* als Informationsbehälter.

--> Jede Produktion bekommt eine Menge von semantischen Regeln die die Berechnung von Attributen beschreiben.

Unterschied semantische und syntaxgesteuerte Definition: Erstere dürfen auch Seiteneffekte haben.

**Synthetisierte Attribute** kommen auf der linken Seite einer Poduktion vor, **vererbte Attribute** auf der rechten Seite.

**Synthetisierte Attribute**

Syntaxgesteuerte Definitionen, in der nur synthetisierte Attribute vorkommen heißen **S-attributierte Definition**.

**Vererbte Attribute**

Sind nützlich "wenn man an ein Symbol Informationen aus dem Kontext, in dem es auftritt, übertragen will".

## 4.2 L-attributierte Definition, Übersetzungsschema

*Übersetzungsschema* erlaubt es mehr Implementierungsdetails auszudrücken. Eine eingeschränkte Klasse von syntaxgesteuerter Definition ist die *L-attributierte Definition* die sich direkt in ein Übersetzungsschema überführen lässt.

Für Bäume gibt es Standard-Durchlaufarten: Breitendurchlauf und Tiefendurchlauf