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
### BlackHoleworld
