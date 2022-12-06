# Projektbericht


## Erklärung Greenfoot

Wir haben uns im Zuge unseres Projekts mit der Umgebung Greenfoot beschäftigt. Genauer gesagt, haben wir ein Spiel mithilfe von Java in Greenfoot programmiert.
Greenfoot ist eine interaktive Java-Entwicklungsumgebung, die besonders für Schüler, Studenten und Programmieranfänger geeignet ist. Mithilfe von vordefinierten Klassen können einfach zweidimensionale graphische Anwendungen wie Spiele oder Simulationen erstellt werden.
Im Prinzip gibt es in Greenfoot „World“- und „Actor“-Klassen. Von beiden lassen sich Unterklassen, sogenannte „Subclasses“ erstellen, die spezifische Eigenschaften besitzen und eine bestimmte Rolle im Spiel erfüllen. 
Eine „World“ ist zweidimensional und ein Ort, in dem die „Actors“ sich befinden und agieren. Ein „Actor“ ist ein Objekt, das in einer „World“ existiert und einen bestimmten Standort hat.
Das Aussehen von „World“- und „Actor“-Objekten lässt sich über ein Icon bestimmen.

## Spiel erklären

Unser Spiel funktioniert folgendermaßen: Man steuert ein Raumschiff - das „Spaceship“- in einer Galaxy. Hier gibt es zwei Level: das erste ist die „Spaceworld“ und das zweite die „BlackHoleworld“. 

Das Ziel ist es, Wale mit dem Raumschiff einzusammeln. Diese tauchen zufälligerweise und verschieden lang in der Welt auf und verschwinden dann wieder von selbst. Wenn das Spaceship einen Wal eingesammelt hat, dann geht der „Score“ um einen Punkt nach oben. Hat man in der „SpaceWorld“ 10 Wale eingesammelt, dann steigt man automatisch ein Level – zur „BlackHoleworld“ – auf, das nach dem gleichen Prinzip funktioniert, wie die „SpaceWorld“, nur schwieriger.

Beim Einsammeln der Wale muss man Asteroiden, die vom linken Bildrand zum rechten ziehen, ausweichen. Denn wenn ein Asteroid und das Raumschiff aufeinander treffen, dann entsteht eine Explosion, ein Explosionsgeräusch ertönt und das Spiel ist verloren und stoppt automatisch.

Hat man 10 Wale in der „SpaceWorld“ und 15 in der „BlackHoleworld“ eingesammelt, dann ist das Spiel gewonnen und ein „Victory“-Banner erscheint.

## Code
### SpaceWorld 

Die „SpaceWorld“ ist eine Subklasse der „World-Klasse“. Der sichtbare Bereich ist 800 mal 400 Pixel groß. Die Welt ist jedoch unendlich groß, weil der Parameter „bounded“ auf „false“ gesetzt wurde.

Die Klasse „SpaceWorld“ hat zwei Variablen, einen „Counter“ und einen „Score“.

Anfänglich steht der Counter auf 0, jedes Mal, wenn die „act“-Methode aufgerufen wird, dann wird der Counter um 1 erhöht. 
Erreicht der Counter ein Vielfaches von 50, dann wird ein neuer Asteroid produziert, der sich auf einer Position links außerhalb des sichtbaren Bereiches und auf einer zufällig generierten Höhe befindet. Es wird sichergestellt, dass der Asteroid sich nicht oberhalb der Welt befindet, indem man als maximalen Wert für die Zufallsgenerierung die Höhe der Welt 
-1 nimmt. 
 
Ähnlich ist das Prinzip bei den Walen, die in der Welt erscheinen, wenn der Counter ein Vielfaches von 60 erreicht. Die Position der Wale wird zufällig generiert, wobei man die Höhe und die Breite der Welt -1 nimmt, um sicherzustellen, dass der Wal sich innerhalb des sichtbaren Bereichs befindet und nicht außerhalb der Welt.

Der „Score“ wird in der Welt angezeigt und immer erhöht, wenn ein Wal vom „Spaceship“ eingesammelt wurde. 
Erreicht der Score 10, dann wechselt das Spiel in das 2-Level, die „BlackHoleworld“.

Mit „fillWorld“ werden die „Actors“ in die Welt positioniert, insbesondere das „Spaceship“ und ein erster „Asteroid“.

Wenn das Spiel gestartet wird, dann wird eine Hintergrundmusik in einer Schleife abgespielt und wenn das Spiel pausiert wird oder endet, endet auch die Musik. 

<details>
	<summary>Ausschnitt des Codes</summary>
 
### BlackHoleworld
### Spaceship
### Asteroid 
### Wale 
### Counter 
### Explosion
### Game Over 
### Victory 
