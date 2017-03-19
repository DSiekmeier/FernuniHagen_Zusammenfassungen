## 2.5 Ströme
*Ströme* sind Datenstrukturen die (vereinfacht) Listen sind. Grundgedanken:

1. Kombination einfacherer Mechanismen und Module zu komplexem Modul
2. Rekursion soll implizit bleiben
3. Kommunikation zwischen Modulen durch Austausch von Folgen von Informationseinheiten

Beispiel: Pipe-Operator | unter UNIX ( p | q )

Für Ströme ist es unerheblich ob diese als parallel oder sequentiell betrachtet werden. p produziert elementweise und q konsumiert elementweise. Diese Art der Kommunikation ist für *Parallelität* grundlegend.

**Implizite Rekursion:** Probleme induktiven Schließens können weitestgehend vermieden werden, Programme terminieren garantiert wenn die vorgegebenen primitiven Elemente garantiert terminieren.

