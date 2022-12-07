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
	
	```J
	
	import greenfoot.*;  // (World, Actor, GreenfootImage, Greenfoot and MouseInfo)

public class SpaceWorld extends World {
    private int counter = 0; 
    private Counter scorecounter = new Counter(); 
    private GreenfootSound music = new GreenfootSound("background.wav");

    public SpaceWorld() {    
        super(800, 400, 1, false);  // Create a new world with 600x400 cells with a cell size of 1x1 pixels.
        fillWorld();
    }

    public Counter getCounter() {
        return scorecounter; 
    }

    public void act() {
        counter = counter +1;
        if (scorecounter.getScore() >= 10) {
            Greenfoot.setWorld(new BlackHoleworld(scorecounter));
        }
        if (counter % 50 == 0) {
            Asteroid myAsteroid = new Asteroid(); 
            addObject(myAsteroid, -20, Greenfoot.getRandomNumber(getHeight()-1)); 
        }
        if (counter % 60 == 0) {
            Wale myWale = new Wale(); 
            addObject(myWale, Greenfoot.getRandomNumber(getWidth()-1), Greenfoot.getRandomNumber(getHeight()-1)); 
        }
    }

    public void fillWorld() {
        addObject (scorecounter, 730,20); 
        Spaceship mySpaceship = new Spaceship(scorecounter);
        addObject(mySpaceship, 600, 200);
        Asteroid myAsteroid = new Asteroid(); 
        addObject(myAsteroid, -20, 100); 
    }

    public void started()
    {
        music.playLoop();
    }

    public void stopped()
    {
        music.stop();
    }
}

	
</details> 
 
### BlackHoleworld

Der Code der „BlackHoleworld“ ist fast identisch zum Code der „SpaceWorld“.

Der erste Unterschied ist, dass die Asteroiden hier öfter generiert werden, nämlich jedes Mal, wenn der Counter ein Vielfaches von 40 ist und die Wale werden seltener generiert, nämlich wenn der Counter ein Vielfaches von 120 ist.

Der zweite Unterschied ist, dass hier beim Erreichen eines Score von 25 der Victory-Banner angezeigt wird, also wenn das Spiel gewonnen ist. 

### Spaceship

Das Raumschiff bekommt den aktuellen Score als Parameter beim Erzeugen des Raumschiffes übergeben. 

Das Raumschiff wird mit den Pfeiltasten gesteuert. Drückt man die rechte Taste, so fährt das Raumschiff rückwärts, drückt man die linke, so steuert es geradeaus. Mit dem Drücken der oberen Taste bewegt es sich nach oben und mit dem Betätigen der unteren, nach unten. 

In der „act“-Methode wird geprüft, ob eine Kollision auftritt. 

Wenn das Raumschiff mit einem Wal in Berührung kommt, wird der Wal entfernt, ein bestimmtes Geräusch wird durch eine eingefügte Wav - Datei abgespielt und ein Punkt wird zum Score hinzugefügt.

Wenn das Raumschiffes mit einem Asteroiden zusammenstößt, also falls die Überprüfung ergibt, dass sich ein Asteroid in der Nähe befindet, dann ist das Spiel automatisch beendet und der GameOver-Banner erscheint. Zudem wird bei dem Zusammenstoß eine Explosion erzeugt.

### Asteroid 

Die Flugrichtung der Asteroiden – von links nach rechts - wird durch den Code festgelegt. 
Wenn ein Asteroid einen Wal berührt, wird der Wal aus der Welt entfernt. 
Darunter wird die Bewegung des Asteroiden definiert; jeder Asteroid addiert pro Durchlauf zwei Längeneinheiten zu seiner X Koordinate. 

### Wale 

Die Lebensspanne ist eine zufällig generierte Zahl zwischen 0 und 500 und definiert die Zeit, wie lange die Wale in der Welt zu sehen sind, bevor sie wieder verschwinden. 

Hierzu gibt es einen Counter der zunächst gleich 0 ist und bei jedem Aufruf der „act“-Methode um 1 erhöht wird. Ist der Counter größer als die Lebensspanne des Wals, wird er entfernt.

### Counter 

Die Klasse „Counter“ zeigt den aktuellen Score an, der zählt wie viele Wale das Spaceship bereits eingefangen hat. Am Anfang steht der Scorecounter auf 0 und geht immer eins hoch, wenn ein Wal gefangen wurde. 

Die Anzeige des Scores erscheint rechts oben in der Farbe weiß auf schwarzem Hintergrund. 

### Explosion

Zunächst einmal gibt es in der Klasse „Explosion“ den Code dafür, dass ein Explosionsgeräusch auftritt, sobald das Spaceship mit einem Asteroiden zusammentrifft. Der Sound wird hierbei durch eine eingefügte Wav-Datei erzeugt. 

Des Weiteren verschwindet das Explosions-Icon, nachdem die „act“-Methode 10-mal aufgerufen wurde, wieder von selbst

### Game Over 

In der Klasse „GameOver“, ist der Code, für die Anzeige des GameOver-Banners, der beim Verlieren des Spiels erscheint, enthalten. Wann der GameOver-Banner erscheinen soll, ist in der Klasse des „Spaceship“ definiert.

### Victory 

In der Klasse „Victory“, ist der Code, für die Anzeige des Victory-Banners, der beim Gewinnen des Spiels erscheint, definiert. Wann der Victory-Banner erscheinen soll, wird von der Klasse „BlackHoleworld“ gesteuert.
