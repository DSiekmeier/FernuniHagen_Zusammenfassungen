# 1 Extreme Programming

- Ende der Neuziger Ruf nach schlankeren Entwicklunsprozessmodellen.
- **Extreme Programming** als Vorreiter der agilen Methoden
- Programmierer und dessen Belange steht im Mittelpunkt
- Diskrepanz zwischen Management und Programmierung (weitgehender Verzicht auf Dokumentation, Planung im Vorfeld, ...)

## 7.1 Geschichte des Extreme Programming

- Erfolg des Buchs stützt sich im Wesentlichen auf ein Projekt von Kent Beck u.A.
- Trend weg von schwergewichtigen Prozessen (wie Wasserfallmodell)
-Extreme Programming ist ein Zusammenspiel von vielen Konzepten und Techniken (On-Site-Customer, Short Releases, Planning Game, Refactoring, Pair Programming, ...)

## 7.2 Ziele des Extreme Programming

- Erstellen von hochqualitativer Software im Zeit- und Kostenrahmen
- Belange des Programmieres stehen im Vordergrund
- wenig Rücksicht auf Belange des Managements
- Erreichung durch *Test-First-Ansatz* und *Programmieren in Paaren*

## 7.3 Der Test-First-Ansatz

- Programmierung und Test oft getrennt voneinander (Programmiert formuliert Tests u.U. unbewusst so, dass kein Fehler augtritt)
- Beim XP liegt Verantwortung für den Code bei allen, somit insbesondere auch beim Programmierer
- Problem der "Blindheit" wird gelöst, indem erst Tests formuliert werden und dann die Funktion implementiert wird
- Hilfreich für Regressionstests
- Andere können Änderungen schnell testen (*Collective-Code-Ownership*): Regressionstests
- Funktionstests sind im Vorfeld verpflichtend und ersetzen (z.T.) auch Spezifikationen
- Kunde ist für die Formulierung der Tests mit verantwortlich

## 7.4 Das Programmieren in Paaren

- Reviews als Teil des Entwicklungsprozesses im XP
- Einer schreibt das Programm und einer schaut zu
- persönliches Verhältnis sollte einigermaßen gut sein
- Zusammensetzung der Teams sollt wechseln

**Vorteile**

- Führt zu höherer Code-Qualität da der Code den Konsens von zwei Programmierern darstellt
- Wissen über den Code ist immer auf mindestens zwei Köpfe verteilt
- ermöglicht gegenseitiges Lernen

## 7.5 Keine Planung

- Motivation für neu Prozessmodelle: Hoher Aufwand von Änderungen bei Fehlern im Code und in der Spezifikation
- Grundannahme beim XP: Änderungen sind billig und jederzeit möglich
- Außer Code praktische keine Dokumentation
- Moderne Werkzeuge für Refactoring notwendig
- Code soll nicht für alle Eventualitäten passen sondern so einfach wie möglich sein
- Weitestgehender Verzicht auf Projektplanung (iterative Softwareentwicklung)
- Anforderungen werden vom Kunden auf Karteikarten formuliert (und im Code formalisiert)
- Mithilfe der Karteikarten kann die Performance der Entwickler gemessen werden
