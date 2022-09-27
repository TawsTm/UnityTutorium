# Unity Tutorium
Dieses Projekt wurde im Rahmen eines Tutoriums an der Hochschule Furtwangen zur Einführung in Unity erstellt.

## 1 Szenen, Objekte und Komponenten
Eine Szene in Unity ist eine Menge von Objekten, die in einer Baumstruktur angeordnet sind. Wenn eine Szene erstellt wird, oder auch die <i>SampleScene</i> mit der ein Projekt beginnt, dann enthält diese bereits zwei Objekte. Jeweils eine <i>Main Camera</i> und ein <i>Directional Light</i>. Die Kamera nimmt das Bild im Spiel auf und das Licht simuliert die Sonne.

![](Images/NewSceneHierarchy.png)

Wenn wir ein Objekt einer Szene hinzufügen wollen geht das über den <b>+</b>-Button vom <i>Hierarchy</i>-Fenster oder Rechtscklick in das Fenster hinein. Dann gibt es die Auswahl zwischen einem leerem Objekt und unterschiedlichen Kategorien von Objekten. Dreidimensionale Körper können in der Kategorie <i>3D Object</i> gefunden werden.

![](Images/Add3DObject.png)

Objekte in einer Szene können untergeordnete Objekte haben, daher die Baumstruktur. Wenn wir einem Objekt ein untergeordnetes Objekt hinzufügen wollen, ist das über Rechtsklick auf das Objekt im <i>Hierarchy</i>-Fenster möglich oder wir ziehen per Drag-and-Drop ein bestehendes Objekt auf ein anderes. Wenn wir Objekte verschieben, drehen oder skalieren wollen, geht das entweder über die Werkzeuge im Szenenfenster oder über die Eigenschaften <i>Position</i>, <i>Rotation</i> und <i>Scale</i> in der <i>Transform</i>-Komponente eines Objekts. Wenn wir Objekten unterschiedliche Farben oder allgemein Oberflächen verpassen wollen, können wir im Projektfenster <i>Materials</i> erstellen und diese per Drag-and-Drop auf das jeweilige Objekt ziehen. Das erstellen von Materials oder anderen Assets im Projektfenster geht über den <b>+</b>-Button, oder indem wir in einem Ordner Rechtsklicken und auf <i>Create</i> gehen. Jetzt können wir zum Beispiel eine Szene mit Würfeln wie in der folgenden Abbildung aufbauen.

![](Images/Scene1.png)

Diese Szene ist bis jetzt noch statisch. Selbst wenn wir im Unity-Editor auf den Play-Button drücken, passiert nichts. In Unity können Objekten über Komponenten Funktionalität hinzugefügt werden. Tatsächlich besitzen die Objekte in dieser Szene schon Komponenten. Die <i>Main Camera</i> hat die Komponenten <i>Camera</i> und <i>Audio Listener</i>, das <i>Direction Light</i> hat die Komponente <i>Light</i> und unsere Würfel haben die Komponenten <i>Mesh Filter</i>, <i>Mesh Renderer</i>, <i>Box Collider</i> und <i>Material</i>. Außerdem hat jedes <i>GameObject</i> in Unity immer eine <i>Transform</i>-Komponente. Wenn wir eine Komponente hinzufügen wollen geht das mit dem <i>Add Component</i>-Button nach der letzten Komponente eines Objekts.

![](Images/AddComponent.png)

Wenn wir jetzt zum Beispiel den Boden drehen lassen wollen, können wir nach einer Komponente <i>RotationAnimator</i> suchen. So eine Komponente gibt es nicht Unity, aber wir haben die möglichkeit über den Button <i>New script</i> ein neues C#-Skript zu erstellen und dieses direkt als Komponente dem Objekt hinzuzufügen. Wenn wir das gemacht haben, finden wir jetzt das Skript auch in dem Projektfenster unter dem Ordner <i>Assets</i>. Hier können wir auf gleiche weise wie <i>Materials</i> auch Ordner erstellen. So kann auch ein Ordner für die C#-Skripte erstellt werden um unser Projekt etwas organisierter zu halten. Mit Doppelklick auf das Skript im Projektfenster oder Klick auf die Pünktchen von der Komponente im <i>Inspector</i> und Auswahl von <i>Edit Script</i>, kann das Skript zur Bearbeitung geöffnet werden. Ein neues Skript sieht vorerst wie in der folgenden Abbildung aus.

![](Images/RotationAnimator1.png)

Wir sehen hier eine Klasse mit dem Namen <i>RotationAnimator</i> wie wir angegeben haben und diese erbt von der Klasse <i>MonoBehaviour</i>, veranschaulicht durch den Doppelpunkt. Durch die Vererbung wird der Klasse alle Grundfunktionalitäten für Skripte in Unity gegeben. Zum Beispiel sind die Methoden <i>Start</i> und <i>Update</i> von MonoBehaviour geerbt. Wichtig zu verstehen ist hier aber erstmal nur wann die Methoden aufgerufen werden. Das steht praktischerweise am Anfang jeweils in der Kommentarzeile über der Methode. Kommentare können in C# mit <i>//</i> angeführt werden. Dadurch wird alles was dahintersteht bei der Ausführung ignoriert und dient somit nur als Information für den Entwickler. Um ein Objekt dauerhaft drehen zu lassen können wir von der <i>Transform</i>-Komponente die <i>Rotate</i>-Methode aufrufen, wie in der folgenden Abbildung zu sehen.

![](Images/RotationAnimator2.png)

Dabei wird, wenn wir runde Klammer auf schreiben, eine Beschreibung der Methode dargestellt bei der wir auch die Parameter sehen. Parameter sind Variablen, die wir in den Runden Klammern an eine Methode übergeben können. In der Regel müssen alle erwarteten Parameter auch übergeben werden, jedoch gibt es sogenannte Überladungen von Methoden. Das sind andere implementierungen einer Methode mit mehr, weniger oder ganz anderen Parametern. So können wir hier auch nur den ersten Parameter <i>eulers</i> angeben. Hier wird ein Objekt des Typs <i>Vector3</i> erwartet. Ein solches Objekt können wir mit <i>new Vector3()</i> erzeugen. Wenn wir hier die Klammer öffnen und eine <i>0</i> schreiben, dann sehen wir die Beschreibung einer Konstruktorüberladung mit drei Parametern <i>x</i>, <i>y</i> und <i>z</i>. Ein Konstruktor ist eine Methode zur Erzeugung eines Objekts von dem entsprechenden Typ. Diese Variante können wir verwenden, um das Objekt zum Beispiel bei jedem <i>Update</i>-Aufruf um 5° um die y-Achse drehen zu lassen.

![](Images/RotationAnimator3.png)

Wenn wir jetzt im Unity-Editor den Play-Button drücken, sehen wir wie sich der Boden mit unserer <i>RotationAnimator</i>-Komponente dreht. Wir sehen auch, dass sich die Würfel auf dem Boden mitrotieren. Das liegt daran, dass sie dem Boden untergeordnet wurden, sie also Kinder des Bodens sind. Dadurch wird die Transformation des Bodens auf die der Würfel übertragen, während die Würfel aber auch individuell relativ zum Boden transformiert sein können. Wir auch einem der Würfel die <i>RotationAnimator</i>-Komponente hinzufügen, dann sehen wir, wie sich der Würfel mit dem Boden rotiert und zusätzlich auf dem Boden rotiert. Jetzt besteht aber das Problem, dass die Geschwindigkeit der Drehung davon abhängt, wie Oft das Bild pro Sekunde aktualisiert wird. Um dieses Problem zu beheben können wir den Vektor, welchen wir an <i>transform.Rotate</i> übergeben, mit <i>Time.deltaTime</i> multiplizieren. <i>Time</i> ist eine Klasse die Unity liefert und die Eigenschaft <i>deltaTime</i> liefert immer die Zeit in Sekunden die vom letzten Frame bis zum Aktuellen vergangen ist. Wenn wir jetzt die Szene abspielen, dreht sich der Würfel langsamer, da die Zeit zwischen zwei Frames weniger als eine Sekunde beträgt. Wir könnten die Geschwindigkeit anpassen, indem wir bei dem Vektor anstatt eine <i>5</i> eine höhere Zahl eintragen, doch wenn die Geschwindigkeit auch noch in Zukunft angepasst wird, müssten wir das Skript jedes Mal neu übersetzen lassen. Beim Übersetzen wird der für uns leserliche Code zu für den Computer ausführbaren Code übersetzt. Dieser Prozess kann viel Zeit kosten, vor Allem wenn häufig neu übersetzt werden muss. Um das zu umgehen können wir der Komponente ein Feld geben, das wir auch im Unity-Editor bearbeiten können. Eine solches Feld kann im Skript mit dem Attribut <i>[SerializeField]</i> angeführt werden. Des Weiteren wird ein Datentyp erwartet. Wir wollen hier eine Geschwindigkeit als Feld definieren und dafür eignet sich eine Fließkommazahl, also geben wir <i>float</i> an. Dann wird nur noch ein Name für das Feld erwartet. Das Feld sollte dann wie folgt im Skript definiert sein.

![](Images/RotationAnimator4.png)

Jetzt müssen wir nur noch den Vektor für die Drehung mit dem neuen Feld <i>speed</i> multiplizieren. Gehen wir zurück zum Unity-Editor sehen wir das Feld <i>speed</i> und wir sollten den Wert auf etwas anderes als 0 ändern, damit sich unser Boden dreht.

![](Images/RotationAnimator5.png)

Wird jetzt die Szene abgespielt dreht sich unser Würfel mit konstanter Geschwindigkeit egal wie schnell die Frames vom Computer berechnet werden. Wir haben außerdem die Möglichkeit während die Szene abgespielt wird das Feld <i>speed</i> zu verändern und sehen direkt den Effekt, also wie sich der Würfel mit der neuen Geschwindigkeit dreht. Um nochmal zu dem Prinzip von untergeordneten Objekten zurückzukehren können wir jetzt auch dem Würfel, der relativ zum Boden rotiert, eine negative Geschwindigkeit geben, sodass dieser sich nicht mehr relativ zur Kamera dreht sondern nur noch verschiebt. Dann sollte der entsprechende Würfel immer richtung Kamera schauen, wie in der folgenden Abbildung zu sehen.

![](Images/Scene1_2.png)


## 2 Physik und Prefabs

Wir haben ja schon gesehen, dass die Würfel, welche wir erstellt haben, <i>Box Collider</i> besitzen. Wir wissen aber noch nicht was sie tun. <i>Collider</i> im allgemeinen werden dazu verwendet zu erkennen, wann Objekte sich berühren. Das ist wichtig um für bewegliche Objekte Hindernisse schaffen zu können. Zum Beispiel wenn wir einen Spielercharakter implementieren wollen müssen wir wissen wann der Charakter anhalten muss, weil eine Wand im Weg ist. Aber auch wenn ein Flummi durch die Szene hüpfen soll sind <i>Collider</i> wichtig, damit der Flummi weiß, wann er abprallen soll. Bis jetzt bewegen sich aber nur die animierten Würfel in unserer Szene und nichts wird von einer Gravitation nach unten gezogen. Um einen frei beweglichen Körper, der an anderen Objekten abprallt, zu simulieren, wie einen Flummi, gibt es in Unity eine weitere Komponente, die <i>Rigidbody</i>-Komponente. Bevor wir aber die Szene verändern, machen wir erst eine Kopie mit <i>strg</i>+<i>d</i> oder <i>strg</i>+<i>c</i> und <i>strg</i>+<i>v</i>. Diese nennen wir dann <i>Szene 2</i> für das zweite Kapitel. In der Kopie können wir dann eine Kugel einfügen, die automatisch mit einem <i>Collider</i> einhergeht und dieser eine <i>Rigidbody</i>-Komponente hinzufügen. Wenn wir sie mit etwas Abstand über den Boden setzen und die Szene abspielen, sehen wir, wie die Kugel abprallt. Jetzt springt die Kugel aber noch nicht wie ein Flummi. Um das zu erreichen müssen wir ein <i>Physic Material</i> erstellen. Hierbei handelt es sich um ein Asset und somit können wir das im Projektfenster erstellen. Im <i>Physic Material</i> können wir die <i>Bounciness</i> als auch andere Eigenschaften einstellen. Dieser Wert geht von 0 bis 1, wenn uns das noch nicht reicht, können wir auch die Methode ändern, wie das Federlevel der beiden kombiniert wird. Das neue Material müssen wir dann beim <i>Collider</i> auswählen. Unsere Kugel kann dann wie folgt konfiguriert sein.

![](Images/BounceBall.png)

Was uns jetzt vielleicht noch auffällt ist die Checkbox für <i>Is Trigger</i> beim <i>Collider</i>. Wenn wir dieses Feld aktivieren, dann wird das Objekt nicht mehr als solides Objekt behandelt sondern als ein begehbarer Raum, welcher aber auf <i>Collider</i> reagiert, die in den Raum rein oder raus gehen. Wir können Mal einen neuen Würfel erstellen bei den wir den <i>Collider</i> zu einem <i>Trigger</i> umschalten. Um zu veranschaulichen, dass der Würfel begehbar ist, erstellen wir ein neues transparentes Material, das wir dem Würfel geben. Wenn jetzt also unser Flummi in den Trigger fliegt, wird er ausgelöst, jedoch haben wir noch nicht implementiert, was in so einem Fall passieren soll. Dafür erstellen wir eine neue Komponente, die wir <i>TriggerListener</i> nennen. Dort wollen wir nicht mehr auf die Ereignisse <i>Start</i> und <i>Update</i> reagieren, also können wir diese Methoden entfernen. Stattdessen fügen wir zwei andere Methoden ein, nämlich <i>OnTriggerEnter</i> und <i>OnTriggerExit</i>. Damit wir ein Feedback bekommen, wenn diese Ereignisse eintreten können wir Debug-Ausgaben einfügen. Das geschieht mit der <i>Log</i>-Methode der von Unity gelieferten Debug-Klasse. Die folgende Abbildung zeigt wie diese Ausgaben aussehen können.

![](Images/TriggerListener1.png)

Wenn wir jetzt die Szene starten und den Flummi in den <i>Trigger</i> fliegen lassen, sehen wir im Fenster der Konsole, dass Ausgaben erfolgen.

![](Images/TriggerListener2.png)

Jetzt haben wir eine Ausgabe, wenn der <i>Trigger</i> ausgelöst wird aber sonst passiert aktuell noch nichts. Wenn wir wollen das ein Objekt verschwindet oder ein Feuerwerk ausgelöst wird, wenn sich ein Objekt in den <i>Trigger</i> hineinbewegt, dann könnten wir das fest als Teil der <i>TriggerListener</i>-Komponente implementieren. Alternativ haben wir aber auch die Möglichkeit einen <i>TriggerListener</i> zu implementieren bei dem erst im Unity-Editor festgelegt wird was beim Eintreten von <i>TriggerEnter</i> und <i>TriggerExit</i> geschehen soll. Hier kommen <i>UnityEvents</i> ins Spiel. <i>UnityEvents</i> können als Felder angelegt werden und werden im Editor sichtbar wie wir es schon mit der Geschwindigkeit vom <i>RotationAnimator</i> gemacht haben. Hierbei wird aber keine Fließkommazahl definiert, sondern eine Liste von Methoden festgelegt, die ausgeführt werden sollen, wenn das jeweilige Ereignis eintritt. Um <i>UnityEvents</i> zu verwenden müssen wir den Namensraum <i>UnityEngine.Events</i>, in dem sie implementiert sind, bekannt machen. Das geht mit dem <i>using</i>-Schlüsselwort wie in der folgenden Abbildung zu sehen.

![](Images/TriggerListener3.png)

Dann fügen wir dem Skript zwei neue Felder <i>TriggerEnterResponse</i> und <i>TriggerExitResponse</i> vom Typ <i>UnityEvent</i> hinzu. Diese können wir dann in den Entsprechenden Methoden, die bis jetzt nur eine Debug-Ausgabe enthalten, auslösen, indem wir jeweils deren <i>Invoke</i>-Methode aufrufen. Das sollte dann wie folgt aussehen.

![](Images/TriggerListener4.png)

Im Unity-Editor können wir jetzt Methoden auswählen die als Antwort auf die Ereignisse ausgeführt werden sollen. Dazu drücken wir den <b>+</b>-Button des jeweiligen Ereignises um einen neuen Eintrag hinzuzufügen. Dort wird als erstes ein Objekt verlangt, von dem wir die Methode ausführen wollen. Zum Testen können wir zum Beispiel die Farbe des Triggers ändern lassen. Dazu ziehen wir per Drag-and-Drop den Trigger selbst als Objekt in den Eintrag und wählen als Methode vom <i>MeshRenderer</i> die Eigenschaft <i>material</i> aus. Hier können wir jetzt noch einen Wert einstellen auf den dann diese Eigenschaft gesetzt werden soll und dazu brauchen wir erst ein neues <i>Material</i>. Wir kopieren das <i>Material</i> des Triggers und ändern dessen Farbe um dann diese Kopie als Wert zu setzen auf den die Eigenschaft <i>material</i> gesetzt werden soll beim Eintreten von <i>TriggerEnter</i>. Bei <i>TriggerExit</i> können wir diese Eigenschaft wieder auf das ursprüngliche Material setzen.

![](Images/TriggerListener5.png)

Wenn jetzt die Szene abgespielt wird sollte sich die Farbe des Triggers ändern, wenn der Flummi reinfliegt und sich wieder zurücksetzen, wenn er rausfliegt. Im Laufe dieses Kapitels haben wir jetzt zwei neue Arten von Objekte erstellt. Zum einen einen Flummi und eine Trigger-Box. Im letzten Kapitel haben wir außerdem drehende Körper erstellt. Aus all diesen Objekten können wir jetzt Prefabs erzeugen. Dazu können wir diese Objekte in der Szene auswählen und per Drag-and-Drop in das Projektfenster ziehen. Wenn wir jetzt kopien dieser Objekte in einer Szene benötigen können wir dessen Prefabs, die jetzt im Projektordner sichtbar sein sollten, genauso per Drag-and-Drop in die entsprechende Szene ziehen. Der Vorteil den wir jetzt haben ist, dass wir nur noch an einer Stelle, innerhalb des jeweiligen Prefabs, Änderungen vornehmen müssen, wenn wir zum Beispiel das Verhalten des Flummis für alle Kopien in allen Szenen verändern wollen. Jetzt brauchen wir nur noch einen Ordner für die Prefabs. Dorthin kann auch das <i>Physic Material</i> des Flummis verschoben werden.

![](Images/PrefabsFolder.png)


## 3 Inputs und Character Movement

Unsere Szene ist mit den neuen Physikobjekten definitiv nicht mehr statisch, doch können wir immer noch nicht mit der Anwendung interagieren. Um Interaktionen zu ermöglichen müssen wir auf <i>Inputs</i> (Eingaben) reagieren. Diese können von verschiedenen Geräten erfolgen z. B. Tastatur, Gamepad oder Android. Hier verwenden wir das neue Input-System von Unity. Das können wir dem Projekt über <i>Window/Package Manager</i> hinzufügen. Der <i>Package Manager</i> spielt in Unity eine wichtige Rolle, da hier viele erweiternde Pakete für das Projekt hinzugefügt werden können. Viele, wie auch das <i>Input System</i>, können schon im Unity Registry gefunden werden. Es gibt aber auch unter <i>Window/Asset Store</i> einen Shop auf dem noch weitere Pakete, darunter auch Levels, 3D-Modelle, Effekte etc., gefunden werden können.

![](Images/WindowTab.png)

Im <i>Unity Registry</i> kann über das Suchfeld nach dem Paket <i>Input System</i> gesucht werden und über den Button <i>instal</i> installiert werden. Danach können wir im Projektordner neue <i>Input Actions</i> erstellen, die wir <i>Player Actions</i> nennen.

![](Images/CreateInputActions.png)

Öffnen wir diese sollten wir folgendes Fenster sehen.
 
![](Images/PlayerActions1.png)
 
Mit dem <b>+</i>-Button fügen wir eine neue <i>Action</i> Map hinzu, die wir <i>Default Actions</i> nennen. Dann fügen wir eine Aktion <i>Look</i> hinzu. Diese Aktion werden wir nutzen, um die Kamera zu schwenken. Das wollen wir über die Bewegung der Maus ermöglichen. Als <i>Action Type</i> wählen wir <i>Value</i> und als <i>Controll Type</i> <i>Vector 2</i>, da wir die Änderung der Position der Maus auslesen wollen (in x- und y-Richtung). Wenn wir <i>Look</i> aufklappen, sehen wir dessen <i>Binding</i>. Hier wählen wir als <i>Path</i> <i>Mouse/Delta</i> aus. Damit haben wir die erste Aktion definiert und können jetzt ein C#-Skript erstellen, das auf diese Aktion reagiert. Um auf eine Input-Aktion zu reagieren, kann eine Methode definiert werden mit einem Parameter <i>context</i> vom Typ <i>InputAction.CallbackContext</i> aus dem Namensraum <i>UnityEngine.InputSystem</i>. Hierfür erstellen wir eine Methode <i>OnInput</i>. Aus dem Parameter <i>context</i> können wir mit der Methode <i>ReadValue</i> den Wert des Inputs auslesen. Dabei müssen wir den Datentyp angeben. Hier geben wir <i>Vector2</i> an, wie wir es bei der Aktion angegeben haben. Der Wert kann schließlich in einem Feld <i>input</i> gespeichert werden.

![](Images/Look1.png)

Jetzt können wir mit <i>transform.Rotate</i> unser Objekt, das die Kamera sein wird, rotieren. Als x-Rotation geben wir <i>input.y</i> und als y-Rotation <i>input.x</i> an. Gehen wir in den Unity-Editor zurück können wir das <i>Look</i>-Skript der Kamera hinzufügen. Noch wird aber die Methode <i>OnInput</i> nicht aufgerufen. Um das zu ändern braucht es noch die Komponente <i>Player Input</i>. Hier können wir unter <i>Behavior</i> <i>Invoke Unity Events</i> auswählen. Dann erscheinen die Ereignisse darunter und können aufgeklappt werden. Unter <i>Default Actions</i> finden wir unsere <i>Look</i>-Aktion und können dem Ereignis einen Methodenaufruf hinzufügen. Von der Kamera kann dann von der Look-Komponente <i>OnInput</i> ausgewählt werden. Da diese Methode einen Parameter vom Typ <i>CallbackContext</i> enthält erscheint sie jetzt ganz oben in der Auswahl. Starten wir die Szene jetzt, können wir die Maus bewegen und sollten sehen wie sich die Kamera entsprechend dreht.

Nachdem wir die Kamera drehen können, wollen wir uns vielleicht auch bewegen können. Dafür gibt es in Unity die Komponente <i>Character Controller</i>. Diese berücksichtigt die Kollision mit anderen Objekten und beinhaltet selbst einen <i>Collider</i>, sodass sich das jeweilige Objekt nicht durch andere Objekte bewegen kann. Der Kamera geben wir ein Elternobjekt das wir <i>Player Character</i> nennen und diesem fügen wir die Komponente hinzu. Jetzt können wir die Kamera bewegen, indem wir die <i>Move</i>-Methode der <i>Character Controller</i>-Komponente aufrufen. Dazu erstellen wir ein neues Skript <i>Move</i> hier fügen wir eine Methode <i>OnInput</i> ein, wie wir sie auch für <i>Look</i> implementiert haben. Dann wollen wir in <i>Update</i> vom <i>Character Controller Move</i> aufrufen. Dazu benötigen wir ein Feld <i>controller</i> vom Typ <i>Character Controller</i>. Die <i>Move</i>-Methode erwartet ein <i>Vector3 motion</i>. Hier erzeugen wir einen neuen Vektor mit <i>input.x</i> als Bewegung in x-Richtung und <i>input.y</i> als Bewegung in y-Richtung. Jetzt muss nur noch wieder die Methode <i>OnInput</i> aufgerufen werden. Dazu definieren wir unter <i>Player Actions</i> eine neue Aktion <i>Move</i>. <i>Action Type</i> und <i>Control Type</i> bleibt gleich wie bei <i>Look</i>. Das <i>Binding</i> entfernen wir aber um ein neues hinzuzufügen. Hier wollen wir <i>Add Up/Down/Left/Right Composite</i> auswählen. Das <i>Binding</i> können wir <i>WASD</i> nennen. Dann müssen wir den vier Richtungen Inputs zuweisen. Dazu klicken wir bei Path auf <i>Listen</i> und drücken dann die gewünschte Taste. Haben wir das gemacht, lässt sich bei der <i>Player Input</i>-Komponente unter <i>Events/Default Actions</i> unsere neue <i>Move</i>-Aktion finden. Hier rufen wir <i>OnInput</i> auf von der <i>Move</i>-Komponente vom <i>Player Character</i>. Spielen wir die Szene ab, können wir uns jetzt auch bewegen, doch wir bewegen uns nicht in die Richtung in die wir schauen. Um dieses Problem zu beheben brauchen wir ein neues Feld im <i>Move</i>-Skript, welches die Transformation der Kamera speichert. Dieses Feld nennen wir <i>lookTarget</i>. Jetzt können wir die Blickrichtung mit <i>lookTarget.forward</i> auslesen und mit <i>lookTarget.right</i> erhalten wir was für die Kamera rechts ist. Die Bewegung können wir jetzt also wie folgt berechnen.

![](Images/Move1.png)

Jetzt können wir uns durch die Szene bewegen, aber wir haben noch keine Interaktionsmöglichkeit außer die Triggerboxen. Wenn wir versuchen uns gegen unseren Flummi zu bewegen, dann halten wir vor ihm an. Das liegt daran, dass die <i>Character Controller</i>-Komponente nicht von sich aus <i>Rigidbodies</i> schiebt. Wenn wir diese Funktionalität haben wollen brauchen wir wieder ein neues Skript. Dieses nennen wir <i>Push</i>. Im Skript können die Methode <i>OnControllerColliderHit</i> einfügen. Diese wird aufgerufen, wenn der <i>Character Controller</i> ein Objekt berührt. Dann können wir vom Parameter <i>hit.collider.attachedRigidbody</i> aufrufen um die <i>Rigidbody</i>-Komponente des berührten Objekts zu erhalten. Jetzt sollten wir noch prüfen, ob diese Komponente überhaupt existiert und ob der Körper auch nicht kinematisch ist. Abfragen lassen sich wie folgt schreiben.

![](Images/Push1.png)

Wenn kein <i>Rigidbody</i> existiert oder der Körper Kinematisch ist, soll die Methode abgebrochen werden. Dafür wird hier die <i>return</i>-Anweisung verwendet. Um jetzt den Körper zu schieben rufen wir <i>AddForce</i> auf. Mit <i>hit.moveDirection</i> erhalten wir die Richtung, in die sich der <i>Character Controller</i> bewegt und somit auch die Richtung in die wir die Kraft anwenden wollen. Jetzt brauchen wir die Richtung nur noch mit einer stärke multiplizieren und wir haben unseren Kraftvektor. Als <i>ForceMode</i> wollen wir <i>Impulse</i> angeben. Fügen wir diese Komponente dem <i>Player Character</i> hinzu und testen nochmal die Szene, sollten wir in der Lage sein den Flummi zu bewegen.


## 4 Scriptable Objects

Wenn wir für Unity eigene Typen von Assets definieren wollen, dann geht das mit <i>Scriptable Objects</i>. Eine Anwendung dafür ist z. B. ein Fließkommawert, der in einem Asset gespeichert ist. Damit könnten wir für unsere erste Szene dafür sorgen, dass wir die Drehgeschwindigkeit nur an einer Stelle ändern müssen, obwohl wir mehrere Würfel mit <i>Rotation Animator</i>-Komponenten drehen lassen. Ein <i>Scriptable Objects</i> erstellen wir in Unity über ein C#-Skript. Hier müssen wir den Typ <i>MonoBehavior</i> auf <i>ScriptableObject</i> ändern, von dem wir erben. In der Klasse wollen wir einfach nur ein Feld <i>value</i> definieren. Um auf den Wert auch von außen zugreifen zu können definieren wir noch eine Eigenschaft mit dem gleichen Namen. Eigenschaften verhalten sich wie Felder in C# und fassen eine Lese- und Schreibmethode zusammen. So können wir mithilfe einer Eigenschaft eine öffentliche Lesemethode für unser nicht-öffentliches Feld definieren. Das sieht dann wie folgt aus.

![](Images/FloatValue1.png)

Damit die Klasse fast fertig. Was noch fehlt ist das Attribut <i>[CreateAssetMenu]</i> vor unserer Klassendefinition. Dadurch wird bei dem <i>Create Asset</i>-Fenster ein Eintrag für unser <i>ScriptableObject</i> gemacht. Wir können jetzt also im Projektordner ein <i>FloatValue</i> erstellen. Diesen nennen wir <i>Rotate Speed</i>. Noch haben wir aber keine Möglichkeit dieses Objekt als Wert von der Geschwindigkeit eines <i>RotationAnimators</i> zu setzen. Dazu müssen wir eine kleine Änderung im Skript machen. Anstatt eine Geschwindigkeit vom Typ <i>float</i> soll es jetzt den Typ <i>FloatValue</i> erwarten. Gehen wir in den Unity-Editor zurück können wir jetzt unser <i>Rotate Speed</i> in das Geschwindigkeitsfeld des <i>RotationAnimators</i> einfügen. Spielen wir die Szene jetzt ab und ändern den Wert von <i>Rotate Speed</i> aktualisiert sich die Geschwindigkeit der Würfel und es drehen sich immer alle gleich schnell. Eine weitere Anwendung sind Ereignisse, die nicht nur innerhalb einer Szene oder eines Prefabs bekannt sein sollen, sondern als Asset im ganzen Projekt. So können wir mehrere Prefabs erstellen, die das gleiche Ereignis auslösen und Prefabs, die auf das gleiche Ereignis reagieren. Hierfür sind zwei Klassen nötig. Einmal ein <i>ScriptableObject Event</i> und ein <i>MonoBehavior EventListener</i>. Für die Implementierung unseres eigenen Events brauchen wir erst einen Methodentyp, den wir in einer Liste speichern und aufrufen können. Um einen Methodentyp zu deklarieren gibt es in C# das Schlüsselwort <i>delegate</i>. Dann schreiben wir wie gewohnt einen Rückgabewert, Namen und die Parameter. Abgeschlossen wird der Typ dann mit einem Semikolon anstatt die Methode mit geschweiften Klammern zu öffnen. Darunter definieren wir ein Feld mit dem Typ <i>List<EventDelegate></i> das direkt initialisiert wird.

![](Images/Event1.png)

Um sich beim Ereignis registrieren zu können fügen wir eine Methode <i>AddListener</i> hinzu. Diese erwartet ein <i>EventDelegate</i>. Bevor wir den <i>Listener</i> unserer Liste hinzufügen, prüfen wir, ob es schon enthalten ist, um zu verhindern, dass <i>Listener</i> doppelt in der Liste vorhanden sind. Elemente können mit der <i>Add</i>-Methode in eine Liste eingefügt werden. Zusätzlich können wir noch eine <i>RemoveListener</i>-Methode schreiben. Um das Ereignis auch auslösen zu können braucht es noch eine <i>Invoke</i>-Methode. Hier wird jeder <i>Listener</i> aufgerufen. Wir können alle Elemente einer Liste mit einer <i>foreach</i>-Schleife durchlaufen. Dabei schreiben wir <i>foreach</i>, runde Klammer auf, die Variable in der immer ein Element der Liste zwischengespeichert werden soll, <i>in</i> und die Liste die wir durchlaufen wollen. Die Klasse sieht dann wie folgt aus.

![](Images/Event2.png)

Beim <i>EventListener</i> benötigen wir ein Feld mit dem Ereignis, auf das reagiert werden soll und ein <i>UnityEvent response</i> als Antwort auf das Ereignis. Dadurch wird wie beim <i>TriggerListener</i> nicht im Skirpt selbst definiert was beim Eintritt des Ereignisses passieren soll, sondern erst im Unity-Editor. Jetzt muss sich der <i>Listener</i> nur beim Ereignis registrieren. Das machen wir bei <i>OnEnable</i>. Diese Methode wird aufgerufen, wenn die Komponente aktiviert wird. Genauso entfernen wir unserere registrierung bei <i>OnDisable</i>. Als <i>EventDelegate</i> können wir dann <i>response.Invoke</i> angeben.

![](Images/EventListener1.png)

Zum Testen können wir unser <i>Trigger</i>-Prefab klonen und diesen <i>Trigger Door</i> nennen. Dann erstellen wir ein Ereignis <i>Door Open</i>. Auf <i>Trigger Enter</i> soll jetzt das Ereignis ausgelöst werden. Danach erstellen wir ein neues Prefab mit einem Würfel, das wir <i>Door</i> nennen. Dieses Prefab soll auch einen <i>EventListener</i> bekommen, welcher auf <i>Door Open</i> hört. Als Antwort soll der <i>Collider</i> und <i>Mesh Renderer</i> deaktiviert werden, sodass die Tür bzw. der Würfel verschwindet. Wenn wir beide Prefabs in eine Szene ziehen und sie starten, sollte die Tür verschwinden, wenn der Trigger von uns ausgelöst wird. Jetzt können wir noch weitere <i>Trigger Door</i>-Objekte und weitere Türen einfügen. Dadurch haben wir jetzt mehre <i>Trigger</i> zur Auswahl, über die sich automatisch alle Türen öffnen, ohne dass wir dafür jeden <i>Trigger</i> einzeln konfigurieren mussten.


## 5 Visual Effect Graph

Jetzt haben wir neue Ereignisse eingefügt, die sich über unsere Trigger aufrufen lassen. Jetzt könnten wir auch auf die Idee kommen ein Feuerwerk auf ein Ereignis starten zu lassen. Für solche Effekte eignet sich der <i>Visual Effect Graph</i> von Unity. Das ist ein Paket im <i>Unity Registry</i>, mit dem sich Partikeleffekte in einem Graphen visuell programmieren lassen. Um das Paket zu nutzen braucht es aber entweder die <i>Universal-</i> oder die </i>High Definition Render Pipeline</i>. Hier verwenden wir die </i>High Definition RP</i>, welche mächtiger ist als die </i>Universal RP</i>, dafür aber weniger, nur leistungsfähigere Geräte unterstützt. Wenn wir beide Pakete installiert haben können wir im Projektordner ein <i>Visual Effect Graph</i> unter dem Eintrag <i>Visual Effects</i> erstellen. Öffnen wir diesen sehen wir folgendes Fenster.

![](Images/Firework1.png)

In einem <i>Visual Effect Graph</i> wird ein Partikelsystem definiert. Ein Partikelsystem verwaltet mehrere Partikel und ist in der Lage diese gleichzeitig zu bewegen und animieren, wobei Partikel einfache Objekte sind, die in der Regel über ein 2D-Bild oder ein 3D-Körper dargestellt werden. Damit können verschiedene visuelle Effekte wie Feuer, Nebel, Explusionen etc. umgesetzt werden. Ein <i>Visual Effect Graph</i> startet mit vier Komponenten. <i>Spawn, Initialize Particle, Update Particle</i> und <i>Output Particel Quad</i>. Dabei verhalten sich <i>Initialize</i> und <i>Update</i> wie <i>Start</i> und <i>Update</i> von <i>MonoBehavior</i> pro Partikel. In <i>Spawn</i> wird definiert, wann wie viele Partikel erzeugt werden. In <i>Output</i> wird festgelegt wie ein Partikel dargestellt wird. Hier können wir die Textur von <i>DefaultParticle</i> zu <i>Default-ParticleSystem</i> ändern. Damit haben wir einen weißen Kreis, der nach außen hin transparent wird. Bei <i>Set Color over Life</i> lässt sich der Farbverlauf für die Partikel einstellen. Bei einem Gradienten wird oben die Transparenz und unten die Farbe festgelegt. So kann der Farbverlauf z. B. wie folgt festgelegt werden.

![](Images/Firework2.png)

Bei Spawn wollen wir anstatt kontinuierlich, auf einen Schlag mehrere Partikel erzeugen. Dafür entfernen wir den aktuellen Block und fügen als neuen Block, <i>Single Burst</i> ein. Bei dem Feld <i>Count</i> können wir dann die Anzahl festlegen. Wichtig ist hierbei, dass nie mehr Partikel, als in <i>Capacity</i> von <i>Initialize Particle</i> definiert ist, gleichzeitig existieren können. Es empfiehlt sich eine Kapazität höher als die <i>Spawn</i>-Anzahl festzulegen, damit das Feuerwerk mehrmals abgespielt werden kann, auch wenn die vorherigen Partikel noch nicht verschwunden sind.

![](Images/Firework3.png)

Um den Effekt in eine Szene einzufügen, können wir ihn per Drag-and-Drop reinziehen. Haben wir den <i>Visual Effect</i> ausgewählt, erscheint ein Fenster mit dem wir den Effekt steuern können. Hier können wir ihn stoppen, pausieren/abspielen, schrittweise abspielen und neu starten. Mit <i>Rate</i> lässt sich die Abspielrate oder auch -geschwindigkeit festlegen. Wenn wir auf <i>Play()</i> oder neu starten klicken, dann sehen wir unseren Partikeleffekt in Aktion. Noch sieht nicht zu sehr nach einem Feuerwerk aus. Wir wollen, dass die Partikel eine Kugel bilden. Dazu müssen wir <i>Set Velocity Random</i> gegen <i>Set Velocity from Direction & Speed</i> tauschen. Dann sollen die Partikel in der Luft abbremsen und von Schwerkraft beeinflusst werden. Hierfür fügen wir bei Update <i>Linear Drag</i> und <i>Gravity</i> ein. Abschließend können wir noch <i>Set Size over Life</i> mit <i>Set Size Random</i> ersetzen. Dadurch haben wir keine Größenänderung sondern unterschiedliche Größen unter den Partikeln. Wenn wir jetzt den Effekt abspielen und etwas die Werte anpassen, sieht unser Feuerwerk schon besser aus.


## 6 Post Processing


## 7 GPU-Events


## 8 Shader Graph
