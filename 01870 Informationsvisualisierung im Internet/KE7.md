# 7 Externe Programmierschnittstellen für VRML und X3D

Behandelt wird das Konzept und die kommerzielle Implementierung der *externen Autorenschnittstelle* (External Authoring Interfac, EAI) von VRML und X3D.

Außerdem *Cortona Automation Interface* (CAI).

## 7.1 External Authoring Interface

VRML / X3D erlaubt bisher objektorientierte Modellierung geometrisch komplexer, virtueller Welten. Repräsentiert durch einen hierachischen Szenengraf. Auch möglich sind Animationen und dynamische Reaktion auf Benutzerinteraktion.

Was fehlt ist Interaktion zwischen Szene und Programm.

EAI ist Programmierschnittstelle des jeweiligen VRML-Browsers zur Kontrolle, Verwaltung und Manipulation der Szene, Ereignissen und der Browserfunktionalität selbst.

- EAI definiert einen programmiertechnischen Laufzeit-Zugang zur VRML-Szene.
- EAI ist Mittler zwischen Java und VRML
- EAI kann von externem Programm oder aus Script-Knoten in der Szene angesprochen werden
- Alle Algorithmen die mit Script-Knoten realisierbar sind, könne auch mit Java-Applet und EAI realisiert werden

- Ausführungsumgebung: EAI außerhalb des Browsers, Script-Knoten innerhalb des Browsers
- Programmrahmen: EAI Java-Applet, Script-Knoten VRML-Szene
- Ereignisbehandlung: EAI asynchron, Script-Knoten synchron

**Komponenten des EAI** sind für den Zugriff auf den aktiven Szenengraf notwendig:

1. Application, beschreibt den externen Prozess
2. Session, Verbindung zwischen genau einem Prozess und einem Browser (Oberbegriff für alle Arten von Verbindungen)
3. Node, kleinste Interaktionseinheit bezogen auf Elemente des Szenengraf
4. Field, stellt eine Eigenschaft eines Knotens dar

TODO

## 7.2 Scene Authoring Interface (SAI)

- Überarbeitung der Schnittstellenspezifikation im Zuge der Weiterentwicklung von VRML zu X3D
- Ziele waren: strengere Typisierung und Unterstützung des Dokumentenobjektmodells (DOM)
- SAI ist integraler Bestandteil aller X3D-Browser
