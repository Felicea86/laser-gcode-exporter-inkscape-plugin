Über dieses Projekt
------------------
Der Zweck dieses Projekts war die Erstellung eines All-in-One-Export-Plugin für Laserschneider und Inkscape 0.91. Es wurde nicht auf niedrigeren Versionen getestet, funktioniert aber möglicherweise..

Das Plugin erstellt GCode, der mit einem Marlin-Fork kompatibel ist, der für die Ausführung auf Laserschneidern entwickelt wurde und unter https://github.com/TurnkeyTyranny/buildlog-lasercutter-marlin zu finden ist.

Sie erreichen mich per Mail unter : 394ad2f@gmail.com. Ich prüfe meine Mails für gewöhnlich täglich.

Spenden
---------
Finden Sie dieses Projekt nützlich? Spenden werden dankbar angenommen. 

* Paypal an 394ad2f@gmail.com
* Bitcoins an 16TFmnFyvDA8Q6TTakvvhargy8c89Rb3cj

Installation
------------

Kopieren Sie die Dateien "turnkeylaser.py" und "turnkeylaser.inx" in Ihren Inkscape Extensions-Ordner -> C:\Program Files\Inkscape\share\extensions.
Starten sie Inkscape und Sie finden das Plugin unter Extensions -> Export -> Turnkey Laser Exporter.

Da dieses Skript auf einer fortgeschritteneren Version der PIL-Bibliothek basiert, als im Lieferumfang von Inkscape für Windows enthalten ist,
müssen Sie für Windows-Installationen von Inkscape 0.91 folgende Schritte befolgen.
Sie haben zwei Möglichkeiten: Wählen Sie diejenige aus, die Ihnen am meisten zusagt.

1) You can alternatively install python on your system, or use my precompiled version. To install python natively :
* besuchen Sie https://www.python.org/downloads/ und laden Sie die 32-Bit Version von Python herunter (https://www.python.org/ftp/python/2.7.9/python-2.7.9.msi) und installieren sie
  unter C:\Python27\ . Wählen Sie während der Installation die Option, Python zu Ihrem Pfad hinzuzufügen.
* Im Ordner : C:\Program Files\Inkscape müssen Sie den Ordner "python" in "python-old" umbenennen, damit stattdessen die neue Systeminstallation verwendet wird.
* Drücken Sie die "Windows-Taste" + "R", um die Befehlszeile zu öffnen, geben Sie "cmd" (ohne Anführungszeichen) ein und drücken Sie die Eingabetaste.
* Führen Sie in der Befehlszeile folgenden Befehl aus: pip install wheel
* Wenn Sie eine Fehlermeldung erhalten, dass pip auf Ihrem System nicht gefunden werden kann, ist Ihr Windows-Pfad falsch. Führen Sie diesen Befehl aus (ohne Anführungszeichen) "set PATH=%PATH%;C:\Python27\;C:\Python27\Scripts" und wiederholen Sie dann den obigen Schritt.
* Laden Sie die Python-Bibliothek von diesem Repo herunter: https://github.com/TurnkeyTyranny/laser-gcode-exporter-inkscape-plugin/blob/master/PIL/Pillow-2.7.0-cp27-none-win32.whl und platzieren Sie sie in einem für Sie einfach zu navigierenden Order, z.B. Ihrem C:\ -Ordner. Alternativ können Sie auch die neuste Version von PIL unter http://www.lfd.uci.edu/~gohlke/pythonlibs/#pil herunterladen.
* Starten Sie die Befehlszeile, indem Sie "Windows-Taste" + "R" drücken, "cmd" eingeben und Eingabe drücken. 
* Navigieren Sie von der Befehlszeile aus zu dem Ort, an dem Sie die Datei abgelegt haben. Wenn Sie sie z.B. im Laufwerk C abgelegt haben, geben Sie ohne Anführungszeichen ein:
* "cd c:\"
* "pip install Pillow-2.7.0-cp27-none-win32.whl"
* Sie müssen außerdem die libxml-Bibliothek installieren. Führen Sie dazu in der Befehlszeile folgenden Befehl (ohne Anführungszeichen) aus:
* "easy_install lxml"
* Fertig! Starten Sie Inkscape und führen Sie das Plugin aus!

![alt tag](https://raw.githubusercontent.com/TurnkeyTyranny/laser-gcode-exporter-inkscape-plugin/master/python_2.7_install.png)
![alt tag](https://raw.githubusercontent.com/TurnkeyTyranny/laser-gcode-exporter-inkscape-plugin/master/command_line_install.png)


2) Wenn Sie 32-Bit Inkscape verwenden, können Sie möglicherweise meine vorkomplilierte Version von 32-Bit-Python mit allen erforderlichen Bibliotheken verwenden. Beolgen Sie folgende Schritte. Dies funktioniert allerdings für einige Leute, für andere jedoch nicht, keine Ahnung warum:
* Laden Sie meine aktualisierte Windows-Version von Python herunter: https://github.com/TurnkeyTyranny/laser-gcode-exporter-inkscape-plugin/blob/master/files/Python27.rar
* Navigieren sie nach C:\Program Files\Inkscape und benennen Sie den Ordner "python" in "python-old"
* Extrahieren sie den Ordner "Python27" aus dem heruntergeladenen Archiv nach C:\Program Files\Inkscape und benennen Sie ihn in "python" um (beachten Sie den Kleinbuchstaben "p")
* Fertig! Starten Sie Inkscape und führen Sie das Plugin aus!
* Wenn Sie das Export-Plugin ausführen und kein Popup-Diagnoseprotokoll mit der Meldung angezeigt wird, welche Elemente erfolgreich exportiert wurden, müssen Sie Python leider manuell installieren wie unten in Option #2 beschrieben.

Linux Installation
------------------
Ausführlichere Anweisungen folgen zu einem späteren Zeitpunkt. Im wesentlichen installieren Sie einfach die PIL-Bibliothek über yum oder apt-get und legen Sie die beiden Skriptdateien (.py and .inx) in Ihrem Erweiterungsverzeichnis ab.

Verwendung und Setup
---------------
Ich empfehle, mit dieser Schnittföäche zu beginnen und Ihre Entwürfe darin anzufertigen. Seine Einrichtung ist auf die Größe des K40-Laserschneidbretts abgestimmt: https://github.com/TurnkeyTyranny/laser-gcode-exporter-inkscape-plugin/blob/master/designs/cutting_surface.svg


Wenn Sie alternativ Ihren eigenen neuen Inkscape Auftrag einrichten, drücken Sie zunächst STRG+UMSCHALT+D, wählen Sie die Registerkarte "Seite" und stellen Sie Ihre Projekteinheiten im Bereich "Benutzerdefinierte Größe" auf "px" ein. Sie können die Option "Standardeinheiten" auf mm, Zoll oder px einstellen. Die "Standardeinheiten" werden auf Ihren Linealen angezeigt.

Geben Sie Ihrer Ebene in Inkscape einen Namen wie: 10 [feed=600,ppm=40]

Dadurch wird die Leistungsstufe auf 10% eingestellt, die Vorschubgeschwindigkeit auf 600 mm pro Minute und es wird mit 40 Impulsen mit einer Dauer von 60 us abgefeuert. Für Raster wird PPM ignoriert.
Die Option "ppm" ist optional. Wenn Sie sie nicht angeben, wechselt der Laser standardmäßig in den Dauerstrichmodus.
Wenn Sie Ihre Ebene nicht auf diese Weise benennen, verwendet das Skript die im Dialogfeld festgelegten Standardeinstellungen.


Wenn Sie bereit sind, Ihre Objekte, Bilder oder Pfade zu exportieren, wählen Sie einfach die Elemente aus, die Sie exportieren möchten, indem sie darüber ziehen oder die Umschalttaste gedrückthalten, um mehrere auszuwählen und dann das Plugin unter Erweiterungsmenü -> Exportieren -> Turnkey Laser Exporter ausführen. 
![alt tag](https://raw.githubusercontent.com/TurnkeyTyranny/laser-gcode-exporter-inkscape-plugin/master/instructions.png)


Die Datei an Ihren Laser senden
------------------------------
Sie können die Datei seriell (USB-Kabel) oder über eine SD-Speicherkarte an Ihren Laser senden.

1) Über USB-Kabel
* Laden Sie Repetier Host herunter und installieren Sie es auf Ihrem PC - http://www.repetier.com/download/
* Öffnen Sie die Software und legen Sie in den Optionen den Anschluss Ihres Lasers fest. Normalerweise handelt es sich dabei um COM7 - ansonsten ist es dasselbe, auf dem Sie Ihren Arduino ursprünglich programmiert haben. Die Portgeschwindigkeit sollte auf 115200 eingestellt sein.
* Drücken Sie die Verbindungstaste. Diese wird grün.
* Öffnen Sie die zuvor erstellte gCode-Datei und klicken Sie auf die Schaltfläche "Drucken". Ihr Laser brennt nun Ihren Befehlssatz.


Alternativ können Sie pronterface verwenden http://www.pronterface.com/index.html#download . Sie müssen sicherstellen, dass Sie das Kontrollkästchen für Pronterface auf der Registerkarte "Erweitert" im Exporter-Plugin aktivieren. Es ist standardmäßig aktiviert.

2) Über SD_Speicherkarte
* Plazieren Sie die Datei auf Ihrer SD-Karte.
* Stecken Sie die SD-Karte in den SD-Kartenleser Ihres Ramps.
* Wählen Sie die Datei aus dem LCD-Menü des Ramps aus und drucken Sie sie aus.

Tastaturkürzel
-----------------

Es kann hilfreich sein, die Erweiterung einer Tastenkombination zuzuweisen. 
Fügen Sie Ihren Inkscape-Schlüsseln etwa die folgende Zeile hinzu 
preferences file (dadurch wird das Plugin an STRG+\ gebunden):

<bind key="backslash" modifiers="Ctrl" action="org.thinkhaus.filter.thlaser"
display="true"/>

Sie finden Ihre Tastatureinstellungsdatei:

* Unter Linux: ~/.config/inkscape/keys/default.xml
* Windows:  %UserProfile%\Application Data\Inkscape\keys\default.xml

Wenn diese Datei nicht existiert, erstellen Sie sie und fügen Sie folgendes ein:

<?xml version="1.0"?>
<keys name="My Keys">
<bind key="backslash" modifiers="Ctrl" action="org.thinkhaus.filter.thlaser"
display="true"/>
</keys>


Quellenangabe
--------------------
Das Projekt basiert auf der Arbeit anderer Leute, der Dank geht an die Mühe, die sie vor mir geleistet haben.

Dank der Arbeit von https://github.com/ajfoul , Thinkhaus und Lansing Makers Network.

Dieses Skript wird unter der Lizenz GPL v2 veröffentlicht.

Change log
--------------------
26-Feb-2015 - 2 hours : Forked from user ajfoul to extend functionality of smoothie laser power levels 0.0 to 1.0, generic Marlin power levels being 0 to 100.

07-March-2015 - 10 hours : Cleaned up the exporters code a lot. Added ppm and feedrate detection from the layer name. Updated the gcode that is exported to be neater and work better with pulsed mode using G01, G02 and G03 commands.

07-March-2015 - Fixed the G28 command at the end of the job. Added defaults for laser power, feedrates and ppm if defined. If ppm isn't defined in the layer options it will operate as continuous wave mode. See the help in the extension dialog for how to use.

07-March-2015 - Marlin codebase mod : You need to patch the Marlin codebase to turn on the laser before moving for G02 and G03 commands. This plugin assumes this has been done. More details to come in the future. Copy the code from the G01 above in marlin_main.cpp - This change has been put into my version of the Marlin Laser firmware found here https://github.com/TurnkeyTyranny/buildlog-lasercutter-marlin

19-March-2015 - After optimising the image to gcode 'code' I'm now working on integrating that into the python script run directly from Inkscape. Hiccups though as Inkscape for Windows ships with a shitty version of Python that is missing imaging libraries. Must install Python 2.7 and PIL for image reading. Have a proof of concept running

20-March-2015 - Added raster support for jpeg and png images. Currently they export at Inkscape's default DPI of 90, I'll have to upscale them to around 300 next. Go burn some cool shit!

27-March-2015 - Objects in inkscape which are not paths are now exported to be rastered. They are exported at 270dpi. Images are now also upscaled or downscaled and exported at 270dpi.

28-March-2015 - Fixed many many bugs with default power levels and other defaults, completed the work on exporting objects and images as rasters. Fixed up as many situations I could find that threw python error messages and replaced them with meaningful notices for the user.

30-March-2015 - Modified the way that X-Y coordinates are determined for a node. This allows objects that are on a layer that has been transposed or transformed or if the objects themselves have to be correctly positioned in the gcode exported data. It's a little bit slower but much more reliable. This change only applies to the export of rasters.

01-April-2015 - Need to get the 'positioning for all' functionality working as exporting many raster objects is painfully slow.
Updated script to export rasters with top left as the origin or bottom left.

09-April-2015 - Updated the readme with better install instructions. Updated the expoter to use a faster method of finding the X-Y coordinates to many rasters however it's only compatible with Inkscape 0.91 now using that command as far as I have been told.

10-April-2015 - Fixed a bug with exporting paths when the origin was the top left.
Disabled raster horizintal movement optimisation as it has a bug. Rasters will be a little slower but will come out oriented correctly. Search for line : row2 = rowData 

11-April-2015 - Added back in raster optimising, it's not perfect but it's mostly there. Only a little slow parsing white vertical space now.
Found that raster optimisation code seems to be changing the pixel data at the end of the line somewhere. I'm not sure how since it's meant to just be cutting part of the data line out not changing it. will need to investigate further.
Added option to the menu for users to disable raster optimisations.
