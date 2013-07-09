---
comments: true
date: 2013-02-21 16:01:26
layout: post
slug: es-ist-ein-himbeerkuchen
title: Es ist ein Himbeerkuchen!
wordpress_id: 595
categories:
- Computer
tags:
- Ampache
- Hörspiele
- Raspberry Pi
- streamripper
---

Zucker spendet Trost, wenn die Laune in den Keller geht -- sei es in Form von Schokolade, Eis oder Kuchen. Mein neuer Himbeerkuchen, der mir über den gestrigen Tag half, hat gottlob keine Kalorien. Hier ein erstes Foto des kleinen Rackers im Einsatz:

![](https://lh6.googleusercontent.com/-yeAzzAe2S6w/USYM2mCjIyI/AAAAAAAABIU/56QW_SllGP8/s1100/21.02.13+-+1)

Jetzt gehöre ich also auch zu den vielen stolzen Besitzern, die ein Bild ihres stromsparenden Lieblings im Internet präsentieren...

<!-- more -->Wie zu sehen sind die Anschlüsse des Pis ziemlich belegt:



	
  1. Eine 16 GB class 10 SD Card dient als Festplatte und Raspbian Wheezy kommt als OS zum Einsatz;

	
  2. ein generisches USB-Netzteil mit 5 V und 1,2 A versorgt den Kleinen zuverlässig mit Strom;

	
  3. per HDMI können bewegte Bilder an meinem Fernseher ausgegeben werden;

	
  4. ein LAN-Kabeln verbindet den Raspi mit Heimnetzwerk und Internet;

	
  5. eine 16 GB USB-Stick dient als Speichererweiterung

	
  6. und ein Logitech Dongle lässt mich über die Logitech K400r mit dem Raspi kommunizieren. Praktischer Weise kombiniert die K400 Tastatur und Touchpad, so dass keine extra Maus benötigt wird.


Die K400r war auch das einzige Problem, auf das ich beim Einrichten des Pis gestoßen bin, denn die Tastatur wollte sich unter [LXDE](http://lxde.org/) partout nicht auf deutsch umstellen lassen. Abhilfe verschaffte eine ~/.xsessionrc, die ich selbst anlegen und mit "**setxkbmap de**" füllen müsste. Nach dem Neustart des X-Servers lief auch unter LXDE die Tastatur einwandfrei. Wird vielleicht wirklich Zeit, dass Wayland kommt und der X-Server sein Altenteil bezieht.

Von der neuen Übertaktungsfunktion, die jetzt offiziell und garantieverlustfrei angeboten wird, habe ich sofort Gebrauch gemacht und so läuft der Raspi mit 1 Ghz anstatt mit 700 Mhz -- konstant und ohne irgendwelche Fehler. Ich bin beeindruckt. Das Übertakten selbst ging ganz einfach, denn es ist nur eine Einstellungen in der raspi-config und die Änderung wird nach einem Neustart aktiv. Ich habe also nie gesehen, wie sich der Rechner mit 700 Mhz schlägt und alle folgenden Aussagen beziehen sich auf ein Modell mit 512 MB RAM und 1 Ghz Taktfrequenz.

Die grafische Oberfläche LXDE läuft erstaunlich zuverlässig auf der vergleichsweise schwachbrüstigen Hardware. Mit Midori lässt sich verhältnismäßig gut surfen, aber es sollten keine Geschwindigkeitswunder erwartet werden: Es dauert halt ein, zwei, drei Sekunden, bis die angeforderte Website erscheint. Aber sie erscheint und lässt sich dann normal nutzen. Wer also nicht auf einen Ferrari zum Surfen angewiesen ist, der oder die kann zum Lesen von heise.de auch problemlos den Raspi nehmen und dabei einiges an Strom sparen. Als Zweitcomputer und Desktopersatz also durchaus denkbar, auch wenn er nicht den Komfort bietet, an den man sich aufschnellen Rechner gewöhnt hat. LibreOffice et al. habe ich noch nicht installiert oder ausprobiert, da ich mit anderen Spielereien beschäftigt war. Dennoch bin ich auf jeden Fall beeindruckt, was das kleine Gerät alles zu leisten im Stande ist.

Kaum stand das Grundsystem kamen auch die ersten Erweiterungen: Der Dateimanager [Midnight Commander](http://www.midnight-commander.org/) für die Konsole wurde ebenso installiert wie das Musikprogramm [moc,](http://moc.daper.net/) damit sich auch MP3s und OGGs abspielen lassen. Schnell per ssh ein paar Lieder vom "großen" Rechner gezogen und et voila, es machte Krach.

Dann folgte die erste (kleine) Herausforderung. Da der Pi lediglich um die 3,5 Watt verbrennt ist er besonders für Einsätze geeignet, für die er rund um die Uhr angeschaltet sein muss. Da ich ja bekannterweise Hörspielliebhaber bin habe ich vor Jahren gelegentlich Radiostreams via [streamripper](http://streamripper.sourceforge.net/) und cron mitgeschnitten, auf Grund des Stromverbrauchs überdimmensionierter Hardware aber wieder davon Abstand genommen. Ich habe mich also gefragt, wie sich der Pi als Streamaufzeichner macht und streamripper installiert.

Was soll ich sagen: Es geht! Er nimmt sogar problemlos mehrere Streams parallel auf und schreibt sie sauber auf den USB-Stick. Mehr noch, er kommt dabei nicht einmal ins Schwitzen, so dass schnell eine zweite Idee in meinem Kopf Gestallt annahm. Wenn ich schon MP3s aufnehme, könnte ich die dann auch über Heimnetzwerk auf andere Geräte streamen? Und wenn ja, wie?

Nach einiger Recherche habe ich mich für den Weg über [Ampache](http://ampache.org/) entschieden, der sowohl Apache Webserver als auch mysql-server voraussetzt. Diese Voraussetzungen schreckten mich anfangs ein wenig ab, weil Programme installieren auf dem Pi ziemlich lange dauert: Der Single-Core Prozessor rechnet eine ganze Weile, bis er die gepackten Binaries aus den Repositorys entpackt hat. Dafür hat Ampache eine gute Infrastruktur, weswegen es sich sowohl via Android als auch via Amarok ansteuern lässt. Naja, während der Pi installiert lässt sich ja auch essen kochen...

Apache, mysql und Ampache ließen sich recht leicht und selbsterklärend einrichten. Zwar gilt auch hier: Wer lesen kann ist klar im Vorteil, aber manchmal will ich eben schneller sein als gut für mich ist. Es läuft jedenfalls und macht, was es soll: streamripper nimmt weiterhin gute Hörspiele auf, Ampache indexiert diese und stellt sie als Stream bereit und ich höre die mir dann einfach als Stream an, wo ich gerade lustig bin. Damit ist das erste Bastelprojekt erstmal abgeschlossen und ich habe eine Konfiguration, die vorerst so weiterlaufen kann, dabei aber kaum Strom verbraucht. Genial.

Ich habe zwar noch überlegt neben Ampache eine eigene OwnCloud aufzusezten, aber 16 GB Speicher fand ich nicht so berauschend viel für eine Cloud und eine externe Festplatte mit eigener Stromversorgung wollte ich nicht anhängen. Also bleibt es erstmal bei 16 GB für Hörspiele. Ansonsten war's das erstmal mit den Basteleien an diesem Pi. Den Rest der Zeit wird er mir erstmal dafür dienen, [Pythen the hard way zu lernen](http://learnpythonthehardway.org/)...
