### Florian, Tobias
# Useless-Box

<h2> Unser Projekt</h2>
Eine Useless Box ist eine Kiste an dessen Oberfläche ein Schalter befestigt ist. Wird dieser betätigt, so öffnet sich der Deckel der Kiste, ein Arm oder ähnliches schnellt herraus und legt den Schalter wieder zurück um. Bekannt wurde dieses Objekt nachdem das Video des YouTube-Nutzers 
 <a href="https://www.youtube.com/watch?time_continue=1&v=Z86V_ICUCD4" rel="notfollow">"Frivolous Engineering"</a> trendete.
<br>
Wir haben uns nun vorgenommen so eine Maschine selber zu bauen.
<br>
Es folgt zu dem Projekt eine <a href="#komponenten">Komponentenliste</a>, eine <a href="#hardware">Bauanleitung für die Hardware</a> und eine <a href="#code">Erklärung des Codes</a>:
<br>
<h2>Inshaltsverzeichnis</h2>
 <ol>
  <li><a href="#komponenten"> Komponenten </a></li>
  <li><a href="#hardware"> Hardware </a></li>
  <li><a href="#code"> Erklärung des Codes </a></li>
   <ol>
    <li><a href="#setup"> Setup-Funktion </a></li>
    <li><a href="#loop"> Loop-Funktion </a></li>
   </ol>
  <li><a href="#endprodukt"> Endergebnis </a></li>
  <li><a href="#quellen"> Quellen </a></li>
 </ol>
</br>
<h2 id="komponenten">Wir benötigen:</h2>
  <li>
   <a href="https://www.conrad.de/de/p/arduino-board-uno-rev3-dip-version-atmega328-1275279.html" rel="notfollow">
    1x Arduino Uno
   </a>
  </li>
  <li>
   <a href="https://www.conrad.de/de/p/graupner-standard-servo-des-577-bb-digital-servo-getriebe-material-carbon-stecksystem-jr-2125787.html" rel="notfollow">
    2x Servo
   </a>
 </li>
 <li>
  <a href="https://www.conrad.de/de/p/tru-components-0165-40-8-8010-steckplatine-transparent-polzahl-gesamt-400-l-x-b-x-h-84-x-54-3-x-9-mm-1-st-1572787.html" rel="notfollow">
   1x Steckbrett
  </a>
 </li>
 <li> 
  <a href="https://www.conrad.de/de/p/goobay-knx-1-kippschalter-250-v-ac-3-a-1-x-ein-ein-rastend-1-st-701343.html" rel="notfollow">
  2x Kippschalter
  </a>
 </li>
 <li>
  Stromversorgung
 </li>
 <li>
  1x Wiederstand
 </li>
 <li>
  Diverse Kabel
 </li>
 <li>
  Holzkiste
 </li>
<br>
<h2 id="hardware">Hardware</h2>
Wir haben zunächst in die Kiste zwei Löcher für die Schalter gebohrt. Als Stromversorgung dient uns ein 7.4V Lipo-Akku. Hier können beliebige Akkus oder Batterien verwendet werden, insofern sie mit der Spannung des Arduinos kompatibel sind. In das Kabel von der Stromquelle zum Arduino wird der erste Schalter reingelötet, welcher die ganze Maschine an und ausschalten kann. Vom Arduino aus wird die Stromversorgung der weiteren Komponenten gesteuert. Der 5-Volt-Pin (5V) bildet den Pluspol und wird an die Plus-Spur des Steckbretts geschlossen. Das Gegenstück dazu ist der Ground-Pin (Grd) welcher den Minuspol darstellt. Dieser wird mit der Minus-Spur verbunden. 
Beide Servos verfügen über jeweils drei Kabel. Plus, Minus und Steuerkabel. Sie sind für jeden Servo definiert, meistens liegt jedoch Plus in der Mitte. Mit Plus und Minus werden die Servos jeweils an die Plus und die Minus-Spur des Steckbretts angeschlossen. Damit haben sie schonmal Strom. Das Steuerkabel, über welches das Eingangssignal kommt, muss nun auch an den Arduino angeschlossen werden. Da es sich bei Servos um ein PWM (Pulse With Modulation) Signal handelt, muss das dritte Kabel beider Servos jeweils an einen PWM-Anschluss des Arduinos. In unserem Falle die Pins 3, 5, 6, 9, 10, 11 und 13. Wir haben sie an die Pins 10 und 11 angeschlossen. Der zweite Schalter ist mit einem Kabel in der Plus-Spur, und leitet den Strom zurück in den Arduino um dort ein Signal auszulösen. In unserem Fall Pin 12. Zwischengeschaltet ist jedoch noch ein Pull-down-resistor, welcher auf dem Steckbrett befestigt ist und dafür sorgt, dass die Restspannung zwischen abgeschaltetem Schalter und Arduino abfließt um eine eindeutige Blockade des Stromflusses am Arduino anzuzeigen. Es geht also ein Kabel aus der Plus-Spur zum Schalter, eins vom Schalter in das Steckbrett, dahinter in die gleiche Reihe auf dem Steckbrett ein Wiederstand welcher in die Minus-Spur führt und hinter den Widerstand ein Kabel, dass in Pin 13 des Arduinos führt. Den Widerstand kann man dabei nicht falschherum einsetzten, da er keine Richtung hat.
An die Servos kommt jeweils noch eine Verlängerung. Für den Servo der den Deckel anhebt ein schlichter Hebel und an den zweiten Servo ein gebogenes Teil, welches über den Rand der Kiste zum Schalter reicht. Befestigt haben wir alle Komponenten mit doppelseitigem Klebeband und Sekundenkleber. Im Deckel der Kiste haben wir noch ein Stück Metall befestigt, was ihn schwerer macht und besser schließen lässt, was aufgrund der vielen Kabel bei uns ein Problem darstellte. Als kleinen Effekt haben wir einen Stoffwurm auf den Servoarm geklebt, welcher dann raus kommt um den Schalter umzulegen.



![Schaltung](https://github.com/Florianovic/Useless-Box-Florian-Tobias/blob/master/fertige%20Schaltung%20ganz.JPG)

![Box](https://github.com/Florianovic/Useless-Box-Florian-Tobias/blob/master/Box%20fertig.jpg)

<br>
<h2 id="code">Der Code</h2>
<p><img width="400px" src="https://github.com/Florianovic/Useless-Box-Florian-Tobias/blob/master/CodeUB.PNG"></p> 
<br>
Als Erstes wird die Datenbank angesteuert, welche benötigt wird um die Servomotoren anzusteuern.<br><br>
#include (Servo.h)
<br>Die Klammern wurden Zwecks Programmfehlers verändert.
<br><br>
Dann wird mit dem nächsten Befehl die Anlaufstelle für den Schalter definiert, welcher am Ende das Skript aktiviert.
<br><br>
const int buttonPin = 12
<br><br>
Als Letztes wird den beiden Servos ein Name zugewiesen. 
<br><br>
Servo h;<br>
Servo z; <br><br>
Wir haben uns der Einfachheit halber für "h" und "z" entschieden. "h" steht hierbei für Hand und "z" für Zunge, da es unser ursprünglicher Plan war, dass der Deckel von einer "Hand" angehoben wird und dann eine "Zunge" herrauskommt und den Schalter wieder umlegt.

<h3 id="setup">Der Setup</h3>
In diesem Schritt wird den Servos eine Anlaufstelle auf dem Arduino zugewiesen und dem Pin 12, an welchem der Schalter befestigt ist, signalisiert, dass an dieser Stelle ein Signal angenommen werden soll, also ein "Input" erwartet wird.<br><br>
h.attach (10); <br>
z.attach (11); <br>
pinMode (buttonPin, INPUT); <br><br>
<h3 id="loop">Der Loop</h3>
Hier ist das Herzstück des Skriptes.<br>
Im ersten Schritt wird festgelegt, dass wenn der Schalter umgelegt wird, also auf "High" gestellt wird, erst Servo "h" sich auf die Position 100 bewegt und den Deckel öffnet, dann eine Pause vonn einer halben Sekunde entsteht (der Arduino zählt in Millisekunden, desshalb 500) und sich schließlich Servo "z" auf die Position 70 bewegt. Das ist gerade so weit, damit der Schalter wieder umgelegt werden kann. <br><br>
if (digitalRead (buttonPin) == HIGH) { <br>
 h.write (100); <br>
 delay(00; <br>
 h.write (70) <br>
} <br><br>
Im zweiten Schritt wird festgelegt, was passiert, wenn der Schalter nicht umgelegt ist oder, wie es in unserem Fall ist, wieder deaktiviert wurde. Zu erst bewegt sich die Servo "z" wieder in ihre Ausgangsposition bei 0. Danach ist wieder eine halbe Sekunde Pause bis sich Servo "h" in Bewegung setzt und sich ebenfalls auf Position 0 bewegt, womit der Deckel wieder geschlossen wird. <br><br>
else{ <br>
 z.write (0); <br>
 delay(500); <br>
 h.write (0); <br>
} <br><br>
<h2 id="endprodukt">Das Endergebnis</h2>
Das Endprodukt spricht für sich; angefügt ist ein Video der Useless-Box in aktion.<br><br>
<p align="center"><a href="https://www.youtube.com/watch?v=3LayQnIBA4o"><img src="https://github.com/tobias2215/InformatikFlorianTobias/blob/master/UB1.PNG" width="400px"><br>Link zum Video</a></p>

<a href="https://github.com/Florianovic/InformatikFlorianTobias">Unser Stundenprotokoll</a>

<h2 id="quellen">Unsere Quellen</h2>
Natürlich haben wir uns im Laufe dieses Projektes an mehreren Quellen bedient um dieses Endprodukt zu Schaffen:
<ul>
 <li>Das <a href="https://www.youtube.com/watch?v=cpdjQ0gheDQ">Video</a> an welchem wir uns orientiert haben</li>
 <li> Die Website von <a href="https://www.arduino.cc/">Arduino</a></li>
 <li>Projekt <a href="https://github.com/lukas2311/Audio_Spectrum_Analyser-Lukas-Torben/blob/master/README.md">"Spektrum-Analyser"</a> für einen großen Teil der Sprache mit welcher GitHub funktioniert</li>
 <li><a href="https://www.youtube.com/watch?v=0wAY3DYihyg&list=PLAB63281B90FB376E">Playlist mit Arduino Tutorials</a></li>
 <li><a href="https://www.youtube.com/watch?v=PrMgJSGK0Ls&t=163s">YouTube Tutorial für die Servos</a></li>
