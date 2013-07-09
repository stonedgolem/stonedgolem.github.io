---
comments: true
date: 2013-03-11 20:09:22
layout: post
slug: horspiele-mitschneiden-mit-dem-pi
title: Hörspiele mitschneiden mit dem Pi
wordpress_id: 643
categories:
- Computer
- Hörspiel
- Software
tags:
- Hörspiele
- öffentlich-rechtlicher Rundfunk
- Raspberry Pi
- Rundfunkstaatsvertrag
- Tutorial
- zeitgesteuerte Aufnahmen
---

Der Raspberry Pi ist schon ein toller Kleinstrechner. Vor allem der geringe Stromverbrauch von gerade mal 3,5 Watt prädestiniert ihn für Einsätze, die einen dauerhaft arbeitenden Rechner erfordern: Ob als kleiner OwnCloud-Server oder für kleinste private Websites, mit dem Pi lassen sich derartige Wünsche schnell und kostengünstig realisieren. Aber auch für Fans der gepflegten, auditiven Unterhaltung eignen sich der Pi hervorragend: Mit nur einem kleinen Programm lassen sich problemlos MP3-Radiostreams aufzeichnen. Dies füllt entweder die Musiksammlung oder den Hörspielordner, je nach dem, zu welchem Zweck das Programm genutzt wird.

<!-- more -->


## Einige Vorbemerkungen: Worum geht's?


Da es genug Websites gibt, die die Aufnahme von Musikradios erklären, möchte ich an dieser Stelle speziell auf die Möglichkeiten zur Hörspielaufnahme eingehen. Alle Radiosender des öffentlich-rechtlichen Rundfunks stehen auch als Stream zur Verfügung, so dass es nahe liegend ist, diese Mitzuschneiden, um kostengünstig die Hörspielsammlung aufzustocken. Allein im deutschsprachigen Raum werden pro Woche um die 50 bis 70 Hörstücke gesendet, unter denen sich einige Perlen finden lassen.

Die meisten dieser Stücke wurden mit Geldern aus der Rundfunkgebühr bezahlt und sollten zumindest meiner Meinung nach ohnehin allen jederzeit und kostenlos zur Verfügung stehen. Geschicktes Taktieren der privaten Rundfunkanstalten verhindert aber, dass die gemeinschaftlich finanzierten Produktionen gesamtgesellschaftlich abrufbar sind. Zwar sieht der aktuelle Rundfunkstaatsvertrag vor, dass Produktionen bis zu sieben Tage online als Download angeboten werden dürfen, aber dies ist trotzdem nicht immer der Fall: So steht der aktuelle "Plan B Krimi" von Eins Live, der den schönen Titel [Road of the Dead](http://www.einslive.de/sendungen/plan_b/krimi/2013/03/130307_road_of_the_dead.jsp) trägt, nur als Stream aber nicht als Download zur Verfügung. Als Begründung werden nur "rechtliche Gründe" angegeben.

Wohl dem also, der sich nicht auf die Gnade der Rundfunkanstalten verlässt! Privatkopien und Rundfunkaufzeichnungen sind in Deutschland <del>noch</del> nicht verboten und es ist dabei sogar egal, ob tatsächlich über Funk, also Radio, oder über's Internet aufgezeichnet wird. Das Mitschneiden der MP3 Streams hat gegenüber Kassetten den deutlichen Vorteil, dass sich die Dateien leicht mit weiteren Programmen bearbeiten und beliebig und ohne Qualitätsverlust auf verschiedenen Datenträgern sichern lassen. Einziger Nachteil: Der Rechner musste immer laufen, was den Stromverbrauch in die Höhe trieb. Die dadurch entstehenden Kosten sind im Vergleich zu den Preisen der Kauffassungen der Radiohörspiele, wie sie beispielsweise der Hörverlag anbietet, nicht sonderlich hoch. Aber wir haben deren Produktion schon mit den Rundfunkgebühren bezahlt und werden dann nochmal zur Kasse gebeten, wenn wir das Hörspiel zu jeder Zeit abspielen wollen.

Wie dem auch sei, mit dem Raspberry Pi minimieren sich jetzt die Stromkosten auf einen Bruchteil und der Aufnahme steht kein schlechtes ökologisches Gewissen mehr im Wege.


## Was wird gebraucht?


Die Liste stellt keine _Minimalkonfiguration_ dar. Um Neulinge nicht zu überfordern werde ich auf den Einsatz von Techniken wie ssh verzichten, denn wer ssh kennt, der oder die wird auch problemlos nachfolgendes mit ssh anwenden können. Wer wirklich viele Hörspiele aufnehmen möchte und den Pi rund um die Uhr als Server für alles mögliche betreibt, sollte sich ohnehin mit Fernadministration auseinander gesetzt haben, da sie das Leben deutlich vereinfachen.

Mit der Aufnahme ist der Pi auch nicht wirklich ausgelastet. Ich betreibe nebenbei noch einen kleinen Webserver, ein Ikiwiki und Ampache auf dem Kleinen und hatte bisher keine Probleme bei der Performance. Auch nicht, wenn ich mehrere Hörspiele parallel mitgeschnitten habe.

Für Menschen, die sich schon ein wenig besser mit Linux auskennen und die schnell wissen wollen, wie sie ihren Pi zum Hörspielrekorder machen, gibt es am Ende des Artikels eine Schnellübersicht der wichtigsten Schritte. Es soll ja niemand gezwungen werden, mehr zu lesen, als notwendig.

Benötigt werden:



	
  * ein Raspberry Pi Model A oder B;

	
  * ein Netzwerkkabel (nur bei Model B) _oder _ein WLAN-Stick zum Verbinden des Pis mit dem Router;

	
  * eine SD-Karte mit einem installierten [Raspbian "wheezy"](http://www.raspberrypi.org/downloads) ([hier gibt es noch ein wenig Hilfe zur Installation](http://elinux.org/RPi_Easy_SD_Card_Setup));

	
  * Tastatur und Maus;

	
  * einen Monitor oder Fernseher;

	
  * ein entsprechendes Kabel, um den Pi an den Monitor zu schließen;

	
  * ein USB-Hub ist beim Model A zwingend erforderlich, da nur ein USB-Port zur Verfügung steht. Beim Model B kann das Hub optional sein. Für den Einsatz des Pis mit ssh kann bei beiden Modellen auf das Hub verzichtet werden.

	
  * Zur Speichererweiterung lässt sich auch optional ein USB-Stick verwenden, auf dem die aufgezeichneten Streams geschrieben werden.




## Installation der benötigten Software


Nachdem der Pi angeschlossen und das Grundsystem mit der [raspi_config](http://raspberrycenter.de/handbuch/grundinstallation-raspi-config) eingestellt wurde, bootet ihr euren Pi ganz normal. Im Grunde ist es egal, ob ihr in die grafische Oberfläche LXDE bootet oder ihr euch mit der Kosoleneingabe begnügt. Da sich dieses Tutorial aber vor allem an Neulinge richtet, gehe ich davon aus, dass LXDE gebootet wurde.

Mit der Grundinstallation von Raspbian wheezy sind die meisten Programme schon enthalten, die wir für unsere Aufgabe benötigen. Lediglich das Programm _streamripper _muss nachinstalliert werden. _streamripper_ ist das Programm, welches später für das Mitschneiden der Streams zuständig sein wird. Damit es_ _installiert werden kann wird eine bestehende Verbindung mit dem Internet benötigt, die auch bei allem, was folgt, als gegeben angenommen wird. Versichert euch also, dass euer Pi mit dem Router verbunden ist und ins Internet gelangt. Am einfachsten lässt sich dies mit einem Raspberry Pi Modell B und einem LAN-Kabel erreichen, welches den Rechner direkt mit eurem Router verbindet.

Öffnet unter LXDE das Programm "LXTerminal". Dieses Programm emuliert eine Kommandozeile, über die ihr die folgenden Befehle an den Rechner übermittelt. Bevor wir aber neue Programme installieren sollte überprüft werden, ob alle Programme auf dem neusten Stand sind. Dazu geben wir folgendes in die Konsole ein:

    
    sudo aptitude update && sudo aptitude safe-upgrade


Im Grunde sind dies zwei Befehle: Der erste weist den Paketmanager _aptitude_ an die neusten Paketlisten zuladen, der zweite Befehl schlägt aktualisierte Pakete zur Installation vor und installiert diese nach eine Bestätigung. Sobald euer System auf dem neusten Stand ist wird es Zeit, _streamripper _zu installieren. Dies ist wiederum einfach mit folgenden Befehl möglich:

    
    sudo aptitude install streamripper


Damit sind wir mit der Vorbereitung der Software auch schon fertig. Auf geht's zum lustigen Timer-Programmieren.


## Zwischenspiel: Was will ich eigentlich aufnehmen?


Spätestens jetzt wird einigen auffallen, dass sie gar nicht die regulären Hörspielzeiten der Radiosender kennen. Oder zwar Zeit und Sender wissen, aber nicht die URL des Streams. Zwar lassen sich alle diese Fragen durch elementares Googlen beantworten, aber auf Dauer wäre das doch ziemlich umständlich. Soviel Mühe muss man sich auch nicht machen, wenn man die [Hörspieldatenbank](http://hoerdat.de/) kennt! Auf dieser Seite finden sich nicht nur Einträge zu vielen deutschsprachigen Hörspielproduktionen sondern auch Informationen zu anstehenden Sendungen des deutschen, österreichisches und schweizerischen Rundfunks! Praktischer Weise mit Sendezeit, geplanter Laufzeit und Link auf den Stream des Senders. Schaut euch ein wenig dort um und sucht euch eine oder mehrere Sendungen raus, die ihr Aufnehmen wollt.

Leider zeigt HoerDat nur Sendungen des öffentlich-rechtlichen Rundfunks an. Private Radiosender wie 89.0RTL spielen gelegentlich Hörspiele oder haben sie zumindest früher mal gespielt. Diese lassen sich zwar ebenso mit streamripper aufnehmen, wenn die URL des Streams bekannt ist, aber die Sendezeiten finden sich nicht bei HoerDat. Dennoch: Eine Übersicht, die besser und vollständiger als HoerDat ist, werdet ihr so schnell nicht finden. Und wenn doch, dann nennt sie mir bitte!


## Aufnahmen mit _streamripper_


_streamripper_ ist eigentlich zur Aufnahme von Musikstücken konzipiert: Im Idealfall läuft das Programm die ganze Zeit und schneidet einen Stream mit, der auf der Festplatte automatisch in kleinere Songdateien aufgespalten wird. Diese Dateien werden anhand der im Stream enthaltenden  ID-Tags benannt, so dass sich die Songs später komfortabel finden lassen. Auch wenn es für einige absonderlich sein mag: _streamripper _hat keine grafische Benutzeroberfläche, sondern es wird komplett in der Kommandozeile ausgeführt und nur über diese gesteuert.

Das Aufteilen der Tracks mag im ersten Moment vielversprechend klingen, bei Hörspielaufnahmen hat es mich immer genervt, weswegen ich die Optionen "-a", "-A", "-s" und "-l" grundsätzlich als Optionen beim Start von _streamripper _angeben. Die Option "-a" sorgt dafür, dass der gesamte Stream in eine einzige MP3-Datei geschrieben wird. Würde ich die Option "-A" weglassen, würden zusätzlich zur großen Datei noch die geteilten Dateien auf die Festplatte geschrieben werden. Ich hätte also alles doppelt gespeichert: Einmal in der großen und einmal in den kleinen Files. Da mir die große Datei zur weiteren Verarbeitung ausreicht verzichte ich also auf das Erstellen der kleinen. Die Option "-s" sorgt dafür, dass kein eigener Ordner mit dem Streamnamen (beispielsweise NDR Info oder SWR) angelegt wird, in dem sich dann die Dateien befinden. Ich nutze diese Option, da ich mit "-d /PFAD/ZUM/ORDNER" schon zuvor festgelegt habe, wo ich die Datei gespeichert haben möchte. Zu guter letzt sorgt die Option "-l" dafür, dass sich _streamripper_ nach der angegebenen Anzahl von **SEKUNDEN **selbst beendet.

Dies sind bei weitem nicht alle Optionen, die _streamripper _bietet. Wer sich für weitere Optionen interessiert, der oder die sollte im Terminal folgendes eingeben:

    
    man streamripper


Mit diesem Befehl wird das Online-Handbuch von _streamripper _angezeigt, das detaillierte Informationen zu allen Optionen bietet.

Kommen wir also zum praktischen Teil und nehmen wir etwas auf. Hierfür müssen wir _streamripper_ mit einem Befehl in der Konsole starten. Dieser Befehl setzt sich im Falle von _streamripper _aus drei Teilen zusammen: Dem Programmnamen _streamripper, _der URL des Streams, der aufgezeichnet werden soll, und weiteren Optionen, die wie der Name schon sagt, optional angegeben werden können.

Folgender Befehl beginnt die sofortige Aufnahme von Deutschlandradio Kultur:

    
    streamripper http://www.dradio.de/streaming/dkultur.m3u


Mit dieser Einstellung wird _streamripper _so lange Deutschlandradio aufnehmen, bis ihr entweder den Rechner ausschaltet oder ihr "Strg+C" im Terminal drückt: Mit dieser Tastenkombination lassen sich alle Programme, die im Terminal ausgeführt werden, beendet. Der Stream wird in eurem Home-Verzeichnis (auch "Persönlicher Ordner" genannt) gespeichert, wo jetzt ein neuer Ordner mit dem Titel "Deutschlanradio Kultur - MP3"erschienen sein sollte.

Mit den schon genannten Optionen würde eine Aufnahme beispielsweise so aussehen:

    
    streamripper http://www.dradio.de/streaming/dkultur.m3u -d /home/pi/DKultur/ -a -A -s -l 4200


Wie zuvor starten wir _streamripper _mit der URL von Dradio Kultur, aber diesmal setzten wir selbst den Ordner und erzeugen dafür den Ordner "DKultur" in unserem Home-Verzeichnis. Sollte der angegebene Ordner beim Start von Streamripper nicht existieren, wird er einfach angelegt, sofern ihr dort Schreibrechte habt. Aber keine Sorge, als Benutzer "pi", der standardmäßig bei Raspbian angelegt ist, habt ihr Schreibrechte im Ordner "/home/pi"und allen darunter liegenden Ordnern. Die Bedeutung der Optionen "-a", "-A" und "-s" habe ich schon erklärt und mit der Option "-l 4200" bricht _streamripper _die Aufnahme nach exakt 4200 Sekunden ab und beendet sich selbst.

Wir könnten nun alle Radiosender beginnen aufzunehmen, die uns interessieren, aber aus Rücksicht auf unsere Festplatte werden wir _streamripper _nicht die ganze Zeit laufen lassen, sondern es zu einer bestimmten Zeit starten und beenden.Wie schon aufgezeigt ist beendet kein Problem, aber leider bietet _streamripper_ keine Option an, dass es sich selbst zu einer bestimmten Zeit startet. Und hier kommt das Programm _cron _ins Spiel.


## Zeitgesteuerte Aufnahmen mit _cron_


_cron _ist ein Systemprogramm von Raspbian, das zeitgesteuerte Aufgaben ausführen kann. In einer Datei wird dafür der Zeitpunkt und die zu erledigende Aufgabe eingegeben. Um in die Tabelle zu gelangen, in der diese angaben zu machen sind, geben wir in der Konsole folgenden Befehl ein:

    
    crontab -e


In der letzten Zeile der Datei, die sich öffnet, können wir eingeben, zu welcher Zeit wir wollen, dass _cron _ohne unser weiteres Zutun _streamripper _ausführt. Um die Funktion von _cron _an reinem Beispiel aufzeigen zu können, nehmen wir an, dass wir am 4. Mai 2013 um 21:05 auf NDR Info das Hörspiel "Kap der Finsternis" aufnehmen wollen. Die Angaben sind übrigens nicht fiktiv und der entsprechende Eintrag in der _crontab _würde so aussehen:

    
    00 21 4 5 * streamripper http://ndrstream.ic.llnwd.net/stream/ndrstream_ndrinfo_hi_mp3 -d /home/pi/Kap_der_Finsternis/ -a -A -s -l 4200


Die Eingaben 00, 21, 4, 5 und * definieren den Zeitpunkt, zu dem _cron_ den nachfolgenden Befehl ausführen soll. Die Zahlen bedeuten dabei folgendes:



	
  * die erste steht für die Minute;

	
  * die zweite für die Stunde;

	
  * die dritte für den Tag des Monats;

	
  * die vierte für den Monat

	
  * und die fünfte für den Tag der Woche.


Ihr seht also, ich lasse die Aufnahme 5 Minute vor dem eigentlichen Sendebeginn beginnen, um damit eventuelle zeitliche Schwankungen zu umgehen. Im Grunde wäre es auch egal gewesen, ob ich die Minute mit "0" oder "00" angegeben hätte: _cron _interpretiert beides als "zur vollen Stunde" und ich schreibe die Doppelnull in der Zeitangabe, weil es für mich auf diese Art lesbarer ist.

Apropos lesbar: Die Angabe "*" bedeutet "egal" bzw. "jeder/jeden". Mit der oben präsentierten Schreibweise habe ich _cron _gesagt, es soll _streamripper _am 4.5. um 21:00 Uhr ausführen und zwar an jedem Wochentag bzw. unabhängig davon, welcher Wochentag es ist. Hätte ich beispeislweise das "*" durch ein "mon" für Montag ersetzt, dann hätte _cron _die Aufgabe nur ausgeführt an einem 4.5., der gleichzeitig ein Montag ist!

Wer sich jetzt über die komische Angabe wundert, dem oder der sei noch gesagt, dass _cron _eigentlich für regelmäßig wiederkehrende Aufgaben entwickelt wurde, die automatisch ausgeführt werden sollten. Eine Zeitangabe wie "00 5 * * mon" ergebt wieder mehr Sinn: Jeden Montag um 5 Uhr soll unabhängig vom Datun ein bestimmtes Programm ausgeführt werden.

Nachdem wie den Eintrag in die _crontab _geschrieben haben, muss diese nur noch gespeichert und geschlossen werden. Wenn ihr ein Standard-Raspbian verwendet, dann wird der Editor höchstwahrscheinlich _nano _sein, der sich bei der Eingabe von "crontab -e" geöffnet hat. In diesem Fall drückt nach der Eingabe einfach "Strg+O" gefolgt von Enter und beendet _nano _mit "Strg+X".

Damit habt ihr euren Pi programmiert das Hörspiel aufzunehmen. Der Rechner wird dies auch zuverlässig machen, sofern er eingeschaltet ist und Internet zur Verfügung hat.

Ich hoffe, ich konnte dir mit diesem Tutorial helfen und dich nebenbei noch ein wenig in die Bedienung von Programmen auf der Kommandozeile einführen. Für alle, die das schon kannten, gibt es hier wie Versprochen die Schnellübersicht:


## Der Raspi als Aufnahmegerät in 6 Schritten:





	
  1. Raspbian installieren und den Rechner ans Netz hängen.

	
  2. Den Rechner mit

    
    sudo aptitude update && sudo aptitude safe-upgrade


aktualisieren.

	
  3. _streamripper_ installieren:

    
    sudo aptitude install streamripper




	
  4. Die _crontab _mit

    
    crontab -e


öffnen, um den Start von _streamripper _zu Programmieren.

	
  5. _crontab _speichern und schließen.

	
  6. Warten, bis die Zeit des Hörspiels gekommen ist, sicherstellen, dass der Raspi über Strom und Internet verfügt und nach der Aufnhame das Hörspiel genießen.


