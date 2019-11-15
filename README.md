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
 </a>
 </li>
 <li>
  Diverse Kabel
 </li>
 <li>
  Holzkiste
 </li>
<br>
<h2 id="hardware">Hardware</h2>
//Hier Text mit Bauanleitung einfügen//
<br>
<h2 id="code">Der Code</h2>
<p><img width="400px" src="https://github.com/Florianovic/Useless-Box-Florian-Tobias/blob/master/CodeUB.PNG"></p> 
<br>
Als Erstes wird die Datenbank angesteuert, welche benötigt wird um die Servomotoren anzusteuern.<br><br>
#include<Servo.h>
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
<p align="center"><a href="https://www.youtube.com/watch?v=3LayQnIBA4o"><img src="https://github.com/tobias2215/InformatikFlorianTobias/blob/master/UB1.PNG" width="400px"><br>Link zum Video</a></p>
<h2 id="quellen">Unsere Quellen</h2>
Natürlich haben wir uns im Laufe dieses Projektes an mehreren Quellen bedient um dieses Endprodukt zu Schaffen:
<ul>
 <li>Projekt <a href="https://github.com/lukas2311/Audio_Spectrum_Analyser-Lukas-Torben/blob/master/README.md">"Spektrum-Analyser"</a> für einen großen Teil der Sprache mit welcher GitHub funktioniert</li>
 <li>[Hier Text einfügen]<a href="Hier Link einsetzen">Name des Objektes</a>...</li>
