# 2 Design by Contract
- Nachteil von Interfaces: lediglich syntaktische Ebene, Verhalten kann nicht mit einer Schnittstelle verbunden werden (Gefahr: Methoden mit gleichem Namen aber unterschiedlichem Verhalten)
- Erster Schritt zur zuverlässigen Software: Festlegung des Verhaltens für jedes Softwareelement (bewirkt nicht automatisch die Einhaltung)

## 2.1 Verhaltensspezifikation durch Zusicherung: Vor- und Nachbedingungen, Invarianten
- Tony Hoare: ```P {A} Q``` (Wenn P vor der Ausführung von A wahr ist, dann ist auch Q wahr)
- P (Vorbedingung) und Q (Nachbedingung) sind logische Ausdrücke (**Zusicherungen**), A eine Folge von **Anweisungen** die eine Zustandsänderung bewirken
- Wird die Vorbedingung nicht eingehalten, ist dies Fehler der Aufruferin, wird die Nachbedingung nicht eingehalten ist dies der Fehler der Aufgerufenen
- Stärkere Vorbedingungen sind schlecht für Aufrufende, stärkere Nachbedingungen sind schlecht für Aufgerufene
- **Invarianten** sind Zusicherungen die durchgängig erfüllt sein müssen (*Klasseninvarianten* müssen für alle Objekte einer Klasse erfüllt sein)
- Während eines Methodenaufrufs können Klasseninvarianten temporär verletzt werden
- Klasseninvarianten, die auf interne Zustände von Objekten zugreifen können heißen *Implementationsinvarianten*
- Vor- und Nachbedingungen, die Teil einer Interfacespezifikation sind, können nur auf öffentliche Eigenschaften einer Klasse zugreifen

## 2.2 Ein paar einfache Beispiele
TODO
