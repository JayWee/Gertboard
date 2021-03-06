# Gertboard Tutorial

<ul>
<li><a href="#1">1. Einleitung</a></li>
<li><a href="#2">2. Inbetriebnahme des Pi</a></li>
<li><a href="#3">3. Aufsetzen von Linux</a></li>
<li><a href="#4">4. Aufsetzen von Windows 10 IoT Core</a></li>
<li><a href="#5">5. Erste Programme mit Phyton über Linux</a></li>
<li><a href="#6">6. Erste Programme mit C# über Windows</a></li>
<li><a href="#7">7. Gertboard</a></li>
<li><a href="#8">8. Einführung </a></li>
<li><a href="#9">9. Nutzung der Buffer </a></li>
</ul>

<h3 id="1">1. Einleitung</h3>

Der Raspberry Pi ist ein Mini-Computer, der vieles von dem, was ein normaler Computer auch kann: Er hat eine graphische Oberfläche1, einen Internetbrowser und andere Programme. 
Es gibt aktuell drei Versionen des Pi, die Funktionen sind größtenteils gleich. Das neueste Modell hat auch WLAN und Bluetooth an Board.


<h3 id="2">2. Inbetriebnahme des Pi</h3>
<p>
Der Pi besitzt keine eigene interne Festplatte oder sonstigen internen Speicher. Deshalb muss man ihm einen stellen. Dies geschieht in Form einer SD-Karte (ab dem Raspberry Pi 2 eine microSD-Karte) mit mindestens 8 GB Speicher (am besten Class 10, bei Windows IoT werden SD-Karten erst ab Class 4 unterstützt).  
Es gibt zwei Betriebssysteme, die Hauptsächlich mit dem Pi benutzt werden. Vor allem ist dies Linux (Raspbian), welches eine vollständige Desktopoberfläche hat. Die Alternative ist Windows 10 IoT Core, welches allerding erst mit ab der 2 Version des Pi für diesen verfügbar ist). Dieses Betriebssystem bietet keine graphische Oberfläche, allerdings kann auf alle Funktion über ein anderen Rechner mit Windows zugegriffen werden. Ebenfalls ist es dann möglich mit [Visual Studio 2015 Community](https://www.visualstudio.com/de/), einem Compiler für diverse Sprachen(C/C#/C++/JavaScript/Visual Basic/Phython) von Microsoft, Remote-Debugging zu betreiben.
</p>

<h4 id="3">Aufsetzten von Linux</h4>

<p>
Als erstes muss eine Installationsdatei für Linux heruntergeladen werden, welches [hier](https://downloads.raspberrypi.org/raspbian_latest) verfügbar ist. Das letztendliche Linux nennt sich Raspbian und ist kostenlos. 
Diese liegt in Form einer einer Zip-Datei, die entpackt werden muss. Anstatt der zip-Datei hat man jetzt eine IMG-Datei. 
Die Sd-Karte muss nun mit dem Computer verbunden werden, um die IMG-Datei drauf zu spielen. 
</p>

<h4>
Windows 
</h4>

<p>
Man installiert nun das Program [Win32DiskImager](http://sourceforge.net/projects/win32diskimager/). Die geladene Datei wird anschließend entpackt und ausgeführt. Mit Hilfe des Programmes installiert man Raspian auf dem Pi. 
</p>


<h4>
Mac
</h4>
<p>
Falls man Raspian mit einem Mac installiert: Als erstes muss sichergestellt werden, dass die SD-Karte im Format MS-DOS (FAT) formatiert ist:  Dafür benutzt man das Festplattendienstprogramm. Dort klickt man auf die SD-Karte an der linken Seite: Wichtig ist, dass man auf die obere klickt, nicht die untere.    
Jetzt wählt man aus der oberen Leiste Löschen aus und dann einen Namen (Ohne Titel), das Format (MS-DOS-Dateisytem (FAT)), und das Schema (GUID). Nun klickt man auf Löschen. 
Jetzt merkt man sich die Zahl die unten rechts im Feld Gerät steht: `diskx`.
Anschließend öffnet man das Terminal (Programme -> Terminal) und gibt den Befehl: `sudo dd bs=1m if=path_of_your_image.img of=/dev/rdiskx` ein.
Statt `path_of_your_image.img` gibt man den Pfad der IMG Datei ein. Diese kann man aus dem Finder kopieren. Dafür wählt man die IMG-Datei aus und rechts-klickt auf die Datei und wählt Informationen aus. Für x setzt man die Zahl aus dem Festpalttendienstprogramm ein und führt den Befehl aus. 
Schlägt der Befehl fehl, kann man statt `rdisk` auch nur `disk` verwenden.
Ist der Befehl ausgeführt, kann die SD-Karte ausgeworfen und in den Pi gesteckt werden. 
</p>
<h3 ref="7">Der erste Start</h3>
<p>
Jetzt steckt man die SD-Karte, auf der das Raspbian installiert ist, in den Pi, der über ein Micro-USB-Kabel mit Strom versorgt wird.  
Nun beginnt der Pi den Startvorgang. In der Zeit sollte man ein LAN-Kabel zur Versorgung mit Internet anschließen. (die Pis der Schule müssen nur angeschlossen werden, sie haben schon Internet. Eigene Pi's müssen erst registriert werden.)
</p>

<h4>
Zugriff auf den Pi 
</h4>
<p>
Der Pi ist nach etwa 2 Minuten bereit um mit ihm zu arbeiten und auf ihn zuzugreifen. Das ist mittels SSH möglich:
Das Herstellen einer SSH-Verbindung zum Rasperry Pi ist sehr nützlich zum Ausführen von Befehlen. Man kann sich dann das anschließen von Monitor und Tastatur an den Pi sparen und vom eigenem Laptop oder Schulrecher aus den Pi steuern.
</p>


<h4>
Verbindung aufbauen
</h4>

<h4>
Linux, macOS
</h4>
<p>
macOS basiert auf Linux und da Linux einen SSH-Klienten mitbringt, gelten diese Schritte auch für macOS.  

Man öffnet das Terminal und führt folgenen Befehlen aus:   
ssh pi@ip  
</p>
<p>
ip ist die Adresse unter der man den Pi erreicht. Man findet sie zuhause über den Router und in der Schule mittels iSurf. 
Man ist nun auf dem Raspberry Pi eingewehlt und kann Befehle und Programme direkt auf dem Pi ausführen. 
Falls man die Verbindung beenden möchte, sendet man entweder den Befehl exit oder schließt das Terminal.
</p>

<h3>
Aufsetzten von Windows 10 IoT Core
</h3>
<p>
Windwos 10 Iot Core ist ein kostenloses Betriebssystem für Kleingeräte von Microsoft ohne graphische richtige Oberfläche (es gibt keinen Desktop für klassische Programme, man kann allerdings Netzwerkeinstellungen auch ohne Konsole machen). Im Gegensatz zum normalen Windows ist IoT Core allerdings darauf spezialisiert LEDs, Sensoren und Motoren anzusteuern. Ebenfalls anders ist, das man per Remote Connection einiges mehr machen kann, als über die eigene Oberfläche. Deshalb kann Windows IoT Core auch mit Geräten genutzt werden, die keinen Bildschirmausgang haben.
</p>

<h4>
Installation auf der SD-Karte
</h4>
<p>
Da IoT Core nur  mit Raspberrys ab der zweiten Generation funktioniert, brauch man auf jeden Fall eine microSD-Karte. Diese muss mindestens 8 GB Speicher haben. Die Daten die noch auf dieser sind werden beim Installieren von IoT Core gelöscht. 
Zum Installieren auf der SD-Karte wird das Programm *[Windows 10 IoT Dashboard](https://developer.microsoft.com/en-us/windows/iot/GetStarted)* benötigt. Die verlinkte Seite enthält ebenfalls eine Anleitung zum Installieren von IoT Core.  
Nach dem installieren dieses Programms muss es geöffnet werden. Unter Gerätetyp dann den Raspberry auswählen. Bei Betriebssystembuild "Windows 10 IoT Core" ausgewählt lassen und bei Laufwerk die SD-Karte auswählen. (Meistens hat das Programm von vornherein schon das Richtige ausgewählt.) Bei Gerätename kann ein beliebiger Name eingesetzt werden. Mit dem gesetzten Administratorpasswort kann man sich dann per Benutzname "administrator" und dem gewählten passwort einloggen. Zum installieren muss dan noch die Lizenzbedingung akzeptiert werden und dann unten rechts auf den Button gedrückt werden.  
</p>
<h4>
Übername von WLAN-Profilen
</h4>
<p>
Wenn auf dem Instalierendem Rechner WLAN-Profile bestehen und entweder ein Model ab Stufe 3 des Raspberrys verwendet wird, oder eein WLAN-Adapter per USB verbunden wurde, können diese dann direkt, oben rechts bei der Installation, mit ünernommen werden. So meldet sich der Pi beim ersten mal Booten direkt per WLAN an und es kann dann auch direkt über siese Verbindung auf ihn zugegriffen werden.  
</p>

<h4>
Zugreifen auf den Pi
Dafür braucht man wieder das Programm *Windows 10 IoT Dashboard*. In diesem geht man auf den Reiter "*Meine Geräte*". Dort wird der Raspberry dann mit dem gegebenem Namen, seinem Typ und der IP-Adresse angezeigt.
</h4>

<h2 name="3">3. Erste Programme mit Phyton über Linux</h2>
<p>
Es ist nun möglich Programme direkt auf dem Pi zu schreiben in dem man die Programmiersprache Python benutzt. 
Man kann aber auch auf dem Mac, auf dem man auch das Terminal ausführt, Programme schreiben.
(Ich empfehle, zum Schreiben von Programmen Xcode zu benutzen, dieses Programm ist kostenfrei im <p><a href="https://itunes.apple.com/us/app/xcode/id497799835?mt=12">MacApp Store</a></p> verfügbar. Auch TextWrangler eignet sich, ist aber ein wenig komplizierter.)
</p>

<h3>  
Anlegen eines Dokuments auf dem Pi
</h3>

Man öffnet das Terminal und führt abermals den Befehl ssh pi@ip aus. Nun loggt man sich mit dem Passwort ein und gibt den Befehl nano Test.py ein. Jetzt öffnet sich der Python-Editor, mit dem man die Programme schreiben kann. Jetzt kann man hier den Code eigegben.

### Das erste Programm 
Möchte man eine LED zum leuchten bringen, schließt man eine LED über ein Jumper-Kabel und einen Widerstand am Pi an. Die Pins die benutzt werden, sind der Ground-Pin und Pin 18. 

Als erstes müssen verschiedene Dinge importiert werden: Die Zeit (time), die Steuerung für die Pins (RPi.GPIO)<!-- und das Einlesen der Tastatur (curses) -->. Das geschieht mit dem Befehl `import Befehl`.

#### Programme schreiben 
Der Anfang des Programmes sieht dann so aus:  
<code>
import RPi.GPIO as GPIO  
import time  
</code>
  
Nun definiert man die Pins als Ausgang-Pins und den GPIO Modus:
<code>
GPIO.setmode(GPIO.BCM)  
GPIO.setwarnings(False)  
GPIO.setup(18,GPIO.OUT) #LED  
</code>

Um die LED zu aktivieren setzt man den output auf HIGH:
<code>
GPIO.output(18,GPIO.HIGH)  
time.sleep(5) #wartet fuenf Sekunden  
GPIO.output(18,GPIO.LOW) #schaltet die LED wieder aus  
GPIO.cleanup() #setzt die Steuerung zurueck  
</code>

Mit crtl-x verlässt man den Editor: Erst *crtl-x* dann *y* und dann *Enter* drücken. Nun gibt man den Befehl `sudo phyton Test.py` ein, um das Programm auszuführen.

Jetzt kann man eine Abfolge von LED leuchten erstellt:	
<code>
GPIO.setup(17,GPIO.OUT) #rot  
GPIO.setup(18,GPIO.OUT) #gelb   
GPIO.setup(27,GPIO.OUT) #gruen   
GPIO.setup(22,GPIO.OUT) #rotf  
GPIO.setup(23,GPIO.OUT) #gruenf  
</code>

Alle als output definiert und dann mittels time.sleep verschiedene Blitzlichter und Morse-Codes erstellt.  
Beispiel SOS:   
<code>
GPIO.output(18,GPIO.HIGH)  
time.sleep(0.5)  
GPIO.output(18,GPIO.LOW)  
time.sleep(0.5)  

GPIO.output(18,GPIO.HIGH)  
time.sleep(0.5)  
GPIO.output(18,GPIO.LOW)  
time.sleep(0.5)  

GPIO.output(18,GPIO.HIGH)  
time.sleep(0.5)  
GPIO.output(18,GPIO.LOW)  
time.sleep(1.5)  

GPIO.output(18,GPIO.HIGH)  
time.sleep(1.5)  
GPIO.output(18,GPIO.LOW)  
time.sleep(0.5)  

GPIO.output(18,GPIO.HIGH)  
time.sleep(1.5)  
GPIO.output(18,GPIO.LOW)  
time.sleep(0.5)  

GPIO.output(18,GPIO.HIGH)  
time.sleep(1.5)  
GPIO.output(18,GPIO.LOW)  
time.sleep(1.5)  

GPIO.output(18,GPIO.HIGH)  
time.sleep(0.5)  
GPIO.output(18,GPIO.LOW)  
time.sleep(0.5)  

GPIO.output(18,GPIO.HIGH)  
time.sleep(0.5)  
GPIO.output(18,GPIO.LOW)  
time.sleep(0.5)  

GPIO.output(18,GPIO.HIGH)  
time.sleep(0.5)  
GPIO.output(18,GPIO.LOW)  
time.sleep(3.5)  
</code>

Um daraus eine Schleife zu machen setzt kann man einen Counter einsetzen. Am Anfang des Programmes `count = 0` setzen und dann `while (count < x):` das sieht dann so aus:  
<code>
count = 0  
while (count < x):
</code>
darunter dann den Inhalt der Schleife setzen. Diese ist jetzt unendlich. Wenn man ans Ende ein `counter += 1` setzt wird der Counter nach jeden Durchlauf um 1 erhöht und das Programm endet nach x Durchläufen. 

`GPIO.setup(2,GPIO.IN)` definiert Pin 2 als Eingang. Das gegegebn kann man mit der Funktion `if GPIO.input(2) == GPIO.HIGH` und einem Schlater eine Ampel bauen. Mit `print "text"` können die einzelnen Schritte in der Konsole beschrieben werden, um ein debugging möglich machen kann.
<code>
import RPi.GPIO as GPIO
import time

GPIO.setmode(GPIO.BCM)  
GPIO.setwarnings(False)  
  
GPIO.setup(17,GPIO.OUT) #rot  
GPIO.setup(18,GPIO.OUT) #gelb  
GPIO.setup(27,GPIO.OUT) #gruen  
GPIO.setup(22,GPIO.OUT) #rotf  
GPIO.setup(23,GPIO.OUT) #gruenf  
  
  
rotan = GPIO.output(17,GPIO.HIGH)  
rotaus = GPIO.output(17,GPIO.LOW)  
gelban = GPIO.output(18,GPIO.HIGH)  
gelbaus = GPIO.output(18,GPIO.LOW)  
greenan = GPIO.output(27,GPIO.HIGH)  
greenaus = GPIO.output(27,GPIO.LOW)  
rotfan = GPIO.output (22,GPIO.HIGH)  
rotfaus = GPIO.output (22,GPIO.LOW)  
greenfan = GPIO.output(23,GPIO.HIGH)  
greenfaus = GPIO.output(23,GPIO.LOW)  
  
count = 0  
while (count < 3):  
    GPIO.output (22,GPIO.HIGH)  
    GPIO.output(27,GPIO.HIGH)    
    if GPIO.input(2) == GPIO.HIGH:  
        print "Signal kommt"  
        GPIO.output(27,GPIO.LOW)  
        GPIO.output(18,GPIO.HIGH)  
        time.sleep(2)  
        GPIO.output(18,GPIO.LOW)  
        GPIO.output(17,GPIO.HIGH)  
        time.sleep(1)  
        GPIO.output (22,GPIO.LOW)  
        GPIO.output (23,GPIO.HIGH)  
        print "Bite gehen"  
        time.sleep(5)  
        print "Bitte nicht mehr gehen"  
        GPIO.output (23,GPIO.LOW)  
        GPIO.output (22,GPIO.HIGH)  
        time.sleep(1)  
        counter +=1  
GPIO.cleanup()
</code>

## 4. Gertboard <a name="4"></a>
![Gertboard Real](https://github.com/JayWee/Gertboard-Tutorial/blob/master/gertboard_real.png)
### Einführung <a name="5"></a>
Das Gertboard von element14 ist ein Erweiterungsboard für alle Versionen des Raspberry Pi. Das Gertboard ist für 26 GPIO-Pins gemacht, passt also perfekt auf die Pins des Raspberry Pi 1 und anderer Modelle des Models A. Bei den B Medelen dagegen sind auf dem Pi 14 Pins mehr, als mit dem Gertboard verbunden werden können.  
Das Gertboard ist mit s. g. Buffern ausgestattet. Diese schützen den Pi bei der benutzung der GPIO-Pins vor Kurzschlüssen. Weiterhin sind auf dem Gertboard noch anschlüsse für eine externe Energiequelle, um Motoren, die eine höhere Spannung brauchen als der Pi liefern kann (3,3V bzw. 5V), mit dem Pi zu betreiben.  

#### Aufbau
![Gertboard Real Blocks](https://github.com/JayWee/Gertboard-Tutorial/blob/master/gertboard_real_blocks.png)
Wie oben in der Graphik zu erkennen ist, ist das Gertboard in sechs Blöcke unterteilt. Diese haben keine Verbindung untereinander.  
Für dieses Tutoral sind nur der schwarze und der rote Block von Relevanz.
Der schwarz umrandete Block umfasst die Verbindung zum Pi (auf der Rückseite) und Pins, die direkt mit den GPIO-Pins auf dem Pi verbunden sind.  
Der rote Block enthält die oben schon erwähnten Buffer, Pins als Ausgänge von den Buffern, Pins zum Einstellen von Input und Output(dies muss im Programm für den Pi selber auch noch mal gemacht werden), 12 LEDs und 3 Druckknöpfe. 
Zusätzlich zu diesen Blöcken gibt es noch die Dauerstrom-Pins (3,3V bzw. 5V).

##### Aufbau der einzelnen Blöcke
Die Platine des Gertboards ist weiß beschriftet. Auf der folgenden Schematik sind nur die Beschriftung und die einzelnen Pins dargestellt:  
![Gertboard Schematisch](https://github.com/JayWee/Gertboard-Tutorial/blob/master/gertboard_shematic.png)  
Blöcke von mehreren Pins sind (Ausgenommen derer in dem Buffer-Block) mit *Jn* (n ist eine natürliche Zahl) beschriftet. Alle Chips auf der Platine sind mit *Un* beschriftet.  
Ganz unten liegt J1. Dies ist die Verbindung zum Pi. Knapp dadrüber liegt J2. Die Pins in diesem Block sind direkt mit den GPIO-Pins des Pi verbunden. 
Weiter wichtig für dieses Tutorial sind die Chips U3-U5. Dies sind die oben genannten Buffer. Ober- und Unterhalb dieser liegen jeweils 8 Pins. Diese sind zur Bestimmung des Modus (Input/Output) gedacht und deshalb mit *out* oder *in* beschrieben. Der Block J3 ist der Eingang zu den Buffern. Die Pins beschriftet mit BUF1-12 sind die Input-Eingänge der Buffer. Zusätzlich zu diesen Input-Pins ist an jeden Buffer-Pin noch eine LED geschaltet und dies ersten drei Buffer Pins (B1-3) sind mit den drei Knöpfen noch verbunden.
Die eben schon erwähnten Dauerstrom-Pins befinden sich in den kleine Böcken J7, J27 und oben links in der Ecke nur 3V3 beschriftet. 

<h4 name="6">Nutzung der Buffer</h4>

<h4> Verbindung mit dem Pi </h4>
Um das Gertboard mit dem Raspberry Pi zu verbinden, muss das Gertboard auf die linken (Der Pi ist so gedreht, dass die Pins oben links liegen) 26 GPIO-Pins gesteckt werden. Bei B Modelen des Pi sind somit die vierzehn rechten Pins nicht mit dem Gertboard verbunden und auf sie kann somit nicht auf dem Gertboard zugegriffen werden. Damit die Buffer-Ausgänge auch Signale senden können müssen bei J7 (3,3V Dauerstrom) zwei der drei Pins miteinander Verbunden werden (am besten mit einem [Jumper](https://github.com/JayWee/Gertboard-Tutorial/blob/master/Shunt-Jumpers2-1383815114.jpg)).    <!---(Für die, die es interessiert: [Warum hier](#10)) -->  

<h4> Arbeiten mit den LEDs und den Druckknöpfen über die Buffer </h4>
Um auf die LEDs zuzugreifen muss erstmal eine Verbindung zwischen den GPIO-Pins (J2) und den Buffer-Eingangs-Pins (J3) hergestellt werden. Jetzt sollten alle LEDs rot leuchten.  
Dann muss der Hardware gesagt werden wie welcher Bufferpin genutzt werden soll (Input/Output). Dafür müssen bei einem Output die beiden Pins, die mit *Bx out* (x ist die Nummer des gewählten Buffereingangs) beschriftet sind, am besten mit einem Jumper verbunden werden. Beim Aufstecken der Jumper, sollte die entsprechende LED ausgehen. Falls nicht, sollte dies spätestens beim starten des Programms passieren.  
Um die Druckknöpfe zu verwenden, muss man über B1-3 darauf zugreifen und entgegen der Tatsache, dass es sich um einen Input handelt, auch einen Jumper bei *Bx out* plazieren (Im Programm müssen die entsprechenden GPIO-Pinsallerdings auf Input gestellt sein). Auf die LEDs der benutzten Knöpfe kann dann nicht mehr zugegriffen werden. Diese Leuchten jetzt beim Starten des Programms. Wenn dann einer der Knöpfe gedrückt wird, geht die entsprechende LED beim Gedrückt sein aus und beim Loslassen wieder an.

<h4> Arbeiten mit externen Geräten über die Buffer </h4>
Wenn mit externen Geräten oder LEDs gearbeitet werden soll, werden nicht beide *Bx out* Pins miteinander verbunden, sondern einer von diesen mit der externen LED. Alle Pins mit dem Senkrecht-Zeichen (umgedrehtes T) oder GND beschriftet sind können als Ground-Pin verwendet werden. Wenn ein Pin als Input genutzt werden soll, wird ein Jumper bei *Bx in* gesetzt und die Input-Quelle mit einem der BUF-Pins.
