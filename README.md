# AVPRG - Beat Laeufer

Beschreibung

Unser Projekt “Beat Läufer” ist ein rhythmus basiertes Spiel. 
Der Spieler produziert Töne und Beats, verbindet diese mit dem Sound der Software und somit entsteht ein vollständiger Song.

Die Spielfigur bewegt sich von links nach rechts über den Bildschirm. Auf der rechten Bildschirmhälfte erscheinen Lücken in unterschiedlichen Farben.
Jede Farbe ist einer Taste zugewiesen und beim drücken wird ein bestimmter Beat oder Ton erzeugt. 
Der Spieler muss nun die passende Taste drücken, wenn der Indikator, der sich vor der Spielfigur befindet, über einer Lücke ist und bevor diese die Spielfigur erreicht. 
Wenn die richtige Taste genau am Anfang der Lücke gerückt wird, ist der Spieler genau im Rhythmus des Songs und somit einen “Perfect Hit”.
Wie näher der Spieler an diesem “Perfekt Hit” ist, sprich wie mehr er im Rhythmus bleibt, desto mehr Punkte bekommt er. Die Punkte des aktuellen “Treffers” werden ihm angezeigt, sowie auch seine bisher gesammelten Punkte.
Am Ende des Liedes wird Ihm eine Bewertung angezeigt mit seiner Gesamtpunktzahl sowie wie oft er welche Art von “Treffer” gesammelt hat.
Der Spieler verliert kontinuierlich “Leben” während des Spiels. Mit jedem erfolgreichen “Treffer” füllt der diese wieder auf. Sollte sein “Leben” auf Null sinken so Ende das Spiel. Dies bestraft den Spieler Falls er zu sehr außerhalb des Rhythmus liegt. Sein aktuelles “Leben” wird ihm in einem Lebensbalken angezeigt.

Insgesamt stehen 3 Level und 2 Lieder über das Hauptmenü zur Auswahl. Jedes Level hat eine unterschiedliche Schwierigkeit und zwischen eins und vier verschiedene Tasten die man verwenden muss. Wie höher die Schwierigkeit desto höher der Beat-Per-Minute des Liedes, die Geschwindigkeit in der die Lücken auf den Spieler zukommen, desto mehr Tasten  und desto kleiner die Lückengröße.


Technische Umsetzung

Das Hauptmenü besteht aus einer einzelnen Seite, die mit Overlays arbeitet um zum Beispiel ein Optionsfenster anzuzeigen. Die Buttons werden hier beim Hovern mit leichten Transition-Effekten animiert . Entscheidet man sich in der 
Levelauswahl für ein Lied, wird man weitergeleitet und der URL erhält den Namen 
des gewählten Levels als Anhang (zB. “game.html?WeWillRockYou”).

Der URL wird zu Beginn des Levels in der Setup-Funktion überprüft und je nach Inhalt wird eine unterschiedliche Level-Datei geladen. Diese Level-Datei beinhaltet die Audiodateien die für dieses Level geladen werden sollen, die Positionen und Farben der Lücken und die Angaben zur Schwierigkeit des Levels, wie die Scroll-Geschwindigkeit und Größe der Lücken. 

Nachdem die Level-Daten geladen und die Lücken in einem Array gespeichert wurden, wird der Gameloop gestartet. Der Spieler und die Plattform mit den Lücken wird auf dem Canvas gezeichnet und jeden Frame wiederholt. Die Position der Lücken wird dabei jedes Mal in der CalcFloor-Funktion neu berechnet und angepasst. Die CalcNextGap-Funktion berechnet zusätzlich welche Lücke die nächste zu treffende Lücke ist und wann es zu spät ist sie noch zu treffen. 

Während des Spielens warten die Keylistener auf den Input des Spielers. Beim Drücken der belegten Tasten wird der dazugehörige Sound abgespielt und die CheckHit-Funktion wird aufgerufen. Die CheckHit-Funktion überprüft ob die korrekte Taste gedrückt wurde und berechnet wie groß der Fehler war. Je näher am perfekten Hit, desto geringer der Fehler. Aus dem Fehler wird anschließend die Punktzahl berechnet, die der letzte Hit dem Spieler gebracht hat. Außerdem wird hier bei korrekten Hits der Lebensbalken ein wenig gefüllt.

Wenn man das Ende des Levels erreicht oder die Lebenspunkte des Spielers auf Null fallen, wird die LevelEnd-Funktion aufgerufen. Diese stoppt die Musik und lässt ein Overlay erscheinen auf dem das Endergebnis angezeigt wird. Hier hat man die Möglichkeit es noch einmal zu versuchen oder ins Hauptmenü zurückzukehren und ein anderes Level zu spielen.
