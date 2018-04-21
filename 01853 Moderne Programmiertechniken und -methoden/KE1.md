# 1 Interfacebasierte Programmierung
- Kein feststehender Begriff, sondern (vorwiegend) von Microsoft geprägt
- Unterstützt Polymorphismus und dynamisches Binden, ohne Vererbung

## 1.1 Der Begriff des Interfaces
- Interfaces sind ein sehr allgemeines Konzept der Informatik
- Parnassches Modularisierungsansatz: jede Entwurfsentscheidung soll hinter Interfaces in Modulen versteckt werden.
- Schnittstellenspezifikationen, die durch Access Modifier an Ort und Stelle implementiert werden: **Klasseninterfaces**

## 1.2 Interfaces als Typen
- Erstmals größere Verbreitung durch Java: Variablen aller Art können mit Interfaces als Typ deklariert werden
- (schwacher) Grund für die Einführung: Ersatz für fehlende Mehrfachvererbung

### 1.2.1 Explizite Interfaceimplementierung
**Prinzip des interfacebasierten Programmierens**
- mehrfache Implementierung der gleichen Signatur wenn verschiedene Interfaces einer Klasse dies verlangen
- Zugriff auf Methoden ausschließlich über

### 1.2.2 Nominale vs. strukturelle Typkonformität
- **nominal**: Implementierung wenn die Klasse dies so deklariert
- **strukturell**: automatische Implementierung aus syntaktischer Gleichheit von Methodendeklaration in Inteface und Klasse
-- Vorteil: offene Systeme bei denen Systemteile dynamisch nachgeladen werden können
-- Nachteil: "zufällige" Implementierungen

### 1.2.3 Interfaces vs. abstrakte Klassen
TODO

## 1.3 Eigenschaften von Interfaces
### 1.3.1 Aufrufen und aufgerufen werden: die zwei Seiten eines Interfaces
TODO
