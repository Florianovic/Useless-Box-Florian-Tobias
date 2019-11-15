### Florian, Tobias
# Useless-Box

<h2> Unser Projekt</h2>
Eine Useless Box ist eine Kiste an dessen Oberfläche ein Schalter befestigt ist. Wird dieser betätigt, so öffnet sich der Deckel der Kiste, ein Arm oder ähnliches schnellt herraus und legt den Schalter wieder zurück um. Bekannt wurde dieses Objekt nachdem das Video des YouTube-Nutzers 
 <a href="https://www.youtube.com/watch?time_continue=1&v=Z86V_ICUCD4" rel="notfollow">"Frivolous Engineering"</a> trendete.
<br>
Wir haben uns nun vorgenommen so eine Maschine selber zu bauen.
<br>
Es folgt zu dem Projekt eine <a href="#komponenten">Komponentenliste</a>, eine <a href="#bauen">Bauanleitung</a> und eine <a href="#code">Erklärung des Codes</a>:
<br>
<h2>Inshaltsverzeichnis</h2>
 <ol>
  <li><a href="#komponenten"> Komponenten </a></li>
  <li><a href="#bauen"> Bauanleitung </a></li>
  <li><a href="#code"> Erklärung des Codes </a></li>
   <ol>
    <li><a href="#setup"> Setup-Funktion </a></li>
    <li><a href="#loop"> Loop-Funktion </a></li>
   </ol>
  <li><a href="#endprodukt"> Endprodukt </a></li>
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
<h2 id="bauen">Bauanleitung</h2>
//Hier Text mit Bauanleitung einfügen//
<br>
<h2 id="code">Der Code</h2>
<br>
Als Erstes wird mit dem Befehl
<p><img width="200px" src="https://github.com/Florianovic/Useless-Box-Florian-Tobias/blob/master/CodeUB%20(2).PNG"></p> 
die Datenbank angesteuert, welche benötigt wird um die Servomotoren anzusteuern.
<br>
<br>
Dann wird mit dem nächsten Befehl die Anlaufstelle für den Schalter definiert, welcher am Ende das Skript aktiviert.
<p><img width="200px" scr="https://github.com/Florianovic/Useless-Box-Florian-Tobias/blob/master/CodeUB%20(3).PNG"></p>
<br>
<h3 id="setup">Der Setup</h3>
