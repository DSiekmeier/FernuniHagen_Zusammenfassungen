## 2.5 Ströme
*Ströme* sind Datenstrukturen die (vereinfacht) Listen sind. Grundgedanken:

1. Kombination einfacherer Mechanismen und Module zu komplexem Modul
2. Rekursion soll implizit bleiben
3. Kommunikation zwischen Modulen durch Austausch von Folgen von Informationseinheiten

Beispiel: Pipe-Operator | unter UNIX ( p | q )

Für Ströme ist es unerheblich ob diese als parallel oder sequentiell betrachtet werden. p produziert elementweise und q konsumiert elementweise. Diese Art der Kommunikation ist für *Parallelität* grundlegend.

**Implizite Rekursion:** Probleme induktiven Schließens können weitestgehend vermieden werden, Programme terminieren garantiert wenn die vorgegebenen primitiven Elemente garantiert terminieren.

### 2.5.1 Homomorphismus auf Strömen

> Ströme sind immer endliche oder unendliche Folge von Daten. Ansätz unterscheiden sich in den angenommenen algebraischen Eigenschaften.

Ein **Homomorphismus h** ist durch Angabe von *combine* und *initial* eindeutig bestimmt. Die Arbeitsweise von h kann als Reduzieren der Ströme von rechts dargestellt werden.

### 2.5.2 Elementweises Abbilden von Strömen
Funktion *map* wendet eine Funktion *f* auf alle Elemente eines Stroms an und liefert Strom zurück.

### 2.5.3 Konkatenation von Strömen
TODO

### 2.5.4 Filtern von Strömen
*filter* erzeugt aus einem Strom *s* alle Ströme *s'* die *p* erfüllen.

### 2.5.5 Konkatenation der Elemente eines Stroms von Strömen
TODO

**Zusammenfassung (Funktionen auf Ströme)**
1. Aufzählen von Strömen: *interval*
2. Elementweises Abbilden: *map*
3. Filtern von Strömen: *filter*
4. Anwendung eines Homomorphismus: *right-reduce*
5. Konkatenation von Strömen: *append-streams*
6. Konkatenieren der Elemente eines Stroms von Strömen: *flatten-streams*

### 2.5.6 Probleme der Implementierung von Strömen durch Listen
Listen sind oft sehr ineffizient, da nur oft nur wenige Elemente des Stroms in das Endergebnis einfließen. Bei langen Strömen werden viele Elemente umsonst berechnet. Da komplexe Programme oft eine Komposition aus einfachen Funktionen ist, treten hier Ströme an den Schnittstellen auf. Diese müssen bei der Listenbetrachtung vollständig im Listenspeicher des Scheme-Systems gespeichert werden.

### 2.5.7 Implementierung von Strömen mit verzögerter Auswertung
Ströme sollten nur soweit berechnet werden, wie es die Funktion die den Strom als Eingang hat erfordert.

> Scheme wertet alle Argumentausdrücke einer Applikation aus, bevor die Auswertung des Funktionsrumpfes beginnt.

Standardtechnik um dies zu verhindern ist das "Verpacken" eines Ausdrucks in eine parameterlose *lambda*-Funktion.

	( lambda ( ) e )

### 2.5.8 Unendliche Ströme
TODO

## 2.6 Zuweisungen und zustandsorientiertes Programmieren
Rein wertorientiertes, also zustandsloses, Programmieren ist nicht immer realistisch. Manchmal ist es effizienter Werte zum Beispiel "vergessen" zu können.

### 2.6.1 Zuweisungsoperationen
**set!** ist elementare zustandstransformiernde Operation. *( set! x e )* weist Wert *e* der Variablen *x* zu. Es ist Konvention zustandsverändernde Operationen (die mit Seiteneffekten) mit einem *!* zu kennzeichnen.

Weitere Zuweisungen: *set-car!* und *set-cdr!*

### 2.6.2 Memo-Funktionen
Memofunktionen haben keinen oder nur einen kleinen, endlichen Parameterwertebereich und speichern das Ergebnis von jedem ihrer Aufrufe. *begin*-Form bewirkt eine sequentielle Auswertung ihrer Parameterausdrücke von links nach rechts.

### 2.6.3 Objektorientierte Programmierung
Bei *Botschaftenorientierter Programmierung* wurden Daten als aktive Objekte behandelt (reagieren typspezifisch auf Nachrichten). Hinzu kommt nun die **Fähigkeit lokale Daten zu ändern**. Objekte haben also zu jeder Zeit einen bestimmten **Zustand**.

## 2.7 Ausblick
### 2.7.1 Programmmodularisierung
### 2.7.2 Typisierung
### 2.7.3 Verzögerte Auswertung
### 2.7.4 Funktionale Sprache Haskell
