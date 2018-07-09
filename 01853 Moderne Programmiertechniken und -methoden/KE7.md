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

## 7.6 Die Kundin vor Ort

- Kunde ist Teil des Projektteams (gegebenenfalls in Stellvertreterposition)
- **Problem:** Person die "alles" beantworten kann ist in der Regel schwer zuu entbehren
- **Kompromiss:** Kunde / Vertretung hat dauerhaften Arbeitsplatz beim Entwickler(team)

## 7.7 gemeinsame Verantwortung

- fehlende Planung bedingt häufige Änderungen die nicht immer vom Autoren des Moduls vorgenommen werden: **der Code gehört allen**
- Konsequenz: **A)** "Wer hat meinen Code verpfuscht?" **B)** Schuldzuweisungen sind nicht förderlich
- Mit Korrektur eines Problems müssen auch Verständnisprobleme beseitigt werden

> Ein stark ausgeprägtes Ego ist beim Extreme Programming hinderlich. Konventionen im Team müssen eingehalten werden.

## 7.8 Der Prozess des Extreme Programming

- Extreme Programming-Prozess ist iterativ: (Zwischen)Produkte werden in regelmäßigen Abständen released
- Ermöglicht kurze Reaktionszeiten des Kunden
- Releases werden in eine bestimmte Anzahl Iterationen unterteilt in denen (in Form von User Stories) bestimmte Funktionalitäten realisiert werden
- Kurze Releasezyklen schaffen Vertrauen und Motivation

## 7.9 Voraussetzungen für den Einsatz von Extreme Programming

- nicht jedes Projekt ist für XP geeignet
- Größe des Teams und damit Projekts ist beschränkt (circa 10 Personen / 3 Jahre Entwicklung)
- **Obergrenze** ist gegeben durch quadratisch mit Teilnehmern wachsendem Kommunikationsaufwand
- **Untergrenze** (2 Teilnehmer) ist gegeben durch gefordertes Pair Programming
- Einsatz moderner Werkzeuge für Refactoring
- Laut Erfinder des XP: OOP notwendig
- keine Altlast-Projekte, da diese nicht einfach geändert werden können
- Bereitschaft nicht unerheblich viel "unproduktiven" Testcode zu schreiben
- XP besonders geeignet wenn Anforderungen im Vorfeld nicht komplett geklärt sind
- Bereitschaft des Kunden zur Mitarbeit ist unabdingbar (Vollzeit-Mitarbeit)

## 7.10 Werkzeuge des Extreme Programming

- Syntaxeditoren mit Auto-Vervollständigung und Codeformatierung
- Refactoring-Werkzeuge
- Versionskontrollee
- Builder

## 7.11 Extreme Programming als risikogetriebene Methode

- Aktivitäten des XP dienen der Risikominderung
- Top-11 der Risiken in der Softwareentwicklung

    *1. Personalknappheit:* Gute Behandlung der MA und Doppelbesetzung

    *2. unrealistische Zeitpläne und Budgets:* inkrementelle Entwicklung

    *3. / 4. Entwicklung falscher Funktionen / Schnittstellen:* "Kunde vor Ort"

    *5. Vergoldung:* Prinzip der Einfachheit

    *6. ständige Anforderungsänderungen:* inkrementelle Entwicklung

    *7. Mängel an 3rd-Party-Produkten:* keine Lösung

    *8. Mängel an 3rd-Party-Leistungen:* keine Lösung

    *9. Mängel am RT-Verhalten:* kurze Release-Zyklen in Produktion

    *10. Anforderungen jenseits Stand der aktuellen Technik:* Explorationsphase zum Projektbeginn

    *11. ändernde Basistechnologien:*

## 7.12 Zusammenfassung

1. Prinzip der kleinen Schritte
2. Prinzip der Einfachheit
3. Prinzip der gemeinsamen Verantwortunk
4. Prinzip des sprechenden Codes
5. Prinzip des Kunden vor Ort
6. Prinzip keine Überstunden
7. Prinzip der Rückkopplung

## 7.13 Übergang zu agilen Prozessen

- Prozessmodell des XP ist starr festgelegt, akribisches Befolgen wird als notwendig angesehen
- moderne agile Prozesse sind weniger dogmatisch
