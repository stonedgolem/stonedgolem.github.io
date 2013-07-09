---
comments: true
date: 2012-05-31 14:13:00
layout: post
slug: ein-ibook-fur-die-masterarbeit
title: Ein iBook für die Masterarbeit
wordpress_id: 82
categories:
- Freie Software
tags:
- Apple
- Debian
- iBook
- Masterarbeit
- MintPPC
---

Ein turbulenter Monat liegt hinter mir, den ich noch genauer im kommenden Monatsrückblick zusammen fassen werde. Eine Veränderungen, die der Mai brachte, möchte ich aber schon jetzt detaillierter Erläutern.

Wie schon mehrfach erwähnt arbeite ich, wenn ich mich nicht gerade auf g+ oder hier rumtreibe, an meiner Masterarbeit. Und eigentlich hatte ich mir zu diesem Zweck einen Laptop fertig gemacht, damit ich außerhalb der Wohnung tippen kann -- vornehmlich an Orten, die weniger Möglichkeiten zur Prokrastination bieten. Dann aber machte sich eben dieser Laptop mit meiner Verlobten im Schlepptau auf den Weg in die freie und Hansestadt Hamburg und ich blieb ratlos zurück. Zwar nicht allein, aber mit Hardware, die mir für meinen Zweck nicht ausreichend erschien, weil sie mehr Ärger über mangelnde Performance als Freude über getippte Seiten in Aussicht stellte. Bis ich eher zufällig auf [MintPPC](http://mintppc.org/) stieß und ich mein uralt iBook G4 aus dem Schrank kramte.

[Linux Mint](http://linuxmint.com/) ist eine Distro, deren Entwicklung ich interessiert verfolge, auch wenn ich sie bisher nicht angetestet habe. Ich kann nicht wirklich sagen wieso aber ich hänge einfach an der Mutter dieser Distros und bleibe wohl noch für eine ganze Weile [Debian Testing](http://debian.org/) treu -- auch, weil Debian mir mein geliebtes [GNOME3](http://gnome.org/) anstatt MATE oder Cinnamon bringt, die ich dann erst wieder löschen müsste. Okay, MintPPC nutzt [LXDE](http://lxde.org/) anstatt GNOME3, aber auf einem Schlepptop mit 1,33 Ghz Prozessor und 512 MB-RAM ist dies auch die bessere Wahl, denke ich.

Das Installationsimage ist mit weniger als 20 MB wirklich klein und schnell runtergeladen. MintPPC holt sich alle Pakete direkt aus dem Netz, weswegen zur Installation unbedingt ein Internetverbindung erforderlich ist. Auch lässt sich der WLAN-Chip nicht während der Installation absprechen, weswegen eine Kabelverbindung zwingend notwendig ist.

Gestern dann also die Installation des neues OS, die auf Grund eines [DAU](http://de.wikipedia.org/wiki/Dümmster_anzunehmender_User)-Fehlers länger dauerte als eigentlich beabsichtigt: Das Netzkabel hatte sich unbemerkt gelöst und der ohnehin angeschlagene Akku war schneller leergeluscht als ich den Fehler bemerken konnte. Die Folge war ein Neustart des Installationsprozesses. Aber von diesen kleinen Hindernissen abgesehen verlief die Installation absolut problemlos und weitgehend automatisiert. Auch Windows-Nutzer würden das hinbekommen -- auf einem [PowerPC](http://de.wikipedia.org/wiki/PowerPC) wohlgemerkt! ;)



Ich präsentiere: Das iBook, welches als Schreibmaschine für meine Masterarbeit auserkoren wurde!


[![](http://2.bp.blogspot.com/-czpNn8UNGY4/T8dGLdahfCI/AAAAAAAAAbY/tfpatqhxZEc/s320/DSC04206.JPG)](http://2.bp.blogspot.com/-czpNn8UNGY4/T8dGLdahfCI/AAAAAAAAAbY/tfpatqhxZEc/s1600/DSC04206.JPG)


Und nutze die Gelgenheit dann auch gleich, ein wenig über meine Erfahrungen zu schreiben, die ich bisher mit MintPPC sammeln konnte.

Was mich sehr überrascht hat: WLAN stand mir anstandslos nach der Installation zur Verfügung. Da ich schon einmal Debian Squeeze mit LXDE auf dem Rechner laufen hatte kenne ich den tückischen WLAN-Chip, der darin werkelt. Die sofortige Einsatzbereitschaft deutet darauf hin, dass unfreie Software eingesetzt wird. Gut für den faulen Endverbraucher, dessen Hardware sofort läuft, weniger gut wenn mensch an die Ideale der Free Software Foundation glaubt. Ich bin jetzt kein Hardcore-Jünger und ein wenig unfreie Software habe ich immer auf dem Rechner, deswegen mecker ich ja nicht -- aber hinweisen möchte ich darauf schon, damit mensch wenigstens _weiß_, dass unfreie Software im Einsatz ist. Bildung ist doch auch etwas, oder?

Etwas verwunderlich fand ich aber die Stille, die mir beim Abspielen von Mediendateien entgegen schwieg. Unter Squeeze hat das iBook ohne zu meckern vor sich hingeplärrt, weswegen ich ein wenig verwirrt war. Es hat einiges Probieren, viele Foreneinträge und den halben Abend gedauert, bis ich dieses Problem beheben konnte: Ich müsste zwei [ALSA](http://www.alsa-project.org/main/index.php/Main_Page)-Module hinzuladen, damit die Soundkarte erkannt wird und angesprochen werden kann. Einen Akkumonitor habe ich nicht, wie mensch noch sehen wird, aber damit kann ich leben, da der eh fast hinüber ist und der Rechner nur mit Netzteil zu gebrauchen ist.

Wer ähnliche Probleme mit dem Sound haben sollte: Bei mir half es, als ich _snd_aoa_i2sbus_ und _snd_aoa_fabric_layout_ zusätzlich in die /etc/modules einzutragen. Nach den Einträgen und einen Neustart war dann die Soundkarte _SoundbyLayout_ im Alsamixer verfügbar, die ich nur noch lautstellen mussten.

[Weitere Lösungsvorschläge lassen sich hier finden](http://oswaldkelso.blogspot.de/2010/10/how-to-fix-no-sound-on-debian-powerpc.html).

Soviel zu den Problemen. Denn das war es auch schon, was ich bisher bemerkt habe: Der Rechtsklick, der bei den Ein-Tasten-Maus-Rechnern von Apple schon immer ein Problem war, ist von Anfang an auf F10 gemappt, alt gr lässt sich mit fn+alt auslösen. Wie gesagt, dies lief sofort, ich musste aber erstmal nachlesen, _dass_ es so ist. Auch der Stromsparmodus beim Schließen des Deckels springt ohne Probleme an und der Rechner erwacht auch wieder flott, wenn man ihn öffnet -- so, als wenn noch OSX darauf laufen würde. Beeindruckend.

Der folgende Screenshot zeigt den Startbildschirm von LXDE nach dem Einloggen:


[![](http://2.bp.blogspot.com/-8D_p7apUD88/T8dCwf4KnSI/AAAAAAAAAas/AFNpdPDFSgc/s320/1.png)](http://2.bp.blogspot.com/-8D_p7apUD88/T8dCwf4KnSI/AAAAAAAAAas/AFNpdPDFSgc/s1600/1.png)


Aufgeräumt und übersichtlich, wie ich es von LXDE gewohnt bin. Im Gegensatz zur "planen" Installation von Debian Squeeze wirkt das angepasste Design von Mint frischer und die gesamte Oberfläche erscheint ein wenig moderner, was schön für's Auge ist, in der Funktionalität aber nichts ändert. Den aufpoppenden Einsteigerguide in der Mitte finde ich gelungen, bietet er doch einen übersichtlichen Anlaufpunkt um sich im neuen System zu orientieren.

Die Softwareauswahl, die MintPPC standardmäßig mitbringt, ist gut und deckt recht viele Einsatzgebiete über die Minimalanforderung Browser/Mailclient hinaus ab. Vor allem die Multimediaauswahl lässt sich sehen:


[![](http://3.bp.blogspot.com/-PcVvmARSLJ0/T8dCw9N0dpI/AAAAAAAAAbo/0WVwo3DCPC0/s320/2.png)](http://3.bp.blogspot.com/-PcVvmARSLJ0/T8dCw9N0dpI/AAAAAAAAAbo/0WVwo3DCPC0/s1600/2.png)





Dank Minitube lässt sich jetzt auch wieder youtube auf dem ollen G4 schauen. Nett. Und mit dem Rest lassen sich ziemlich viele Multimediaeinsätze abdecken.

Im Bürobereich wird auf Open oder Libre Office verzichtet und lediglich Abiword und Gnumeric serienmäßig geliefert. Dies ist sicherlich der gealterten Hardware geschuldet, die schon ein wenig Rechnen muss um Apache Open Office oder Libre Office zu öffnen. Wer auf die großen Büropakete nicht verzichten möchte kann diese wie gewöhnt über die Softwareverwaltung nachinstallieren.

Software, die dem Linux Mint Projekt entspringt, habe ich nur bei der Softwareverwaltung gefunden.


[![](http://4.bp.blogspot.com/-mhQDUKP7KJ0/T8dCxs_2u2I/AAAAAAAAAa4/N0JkBv4ACaY/s320/4.png)](http://4.bp.blogspot.com/-mhQDUKP7KJ0/T8dCxs_2u2I/AAAAAAAAAa4/N0JkBv4ACaY/s1600/4.png)


Als beinharter aptitude-Terminal-Junkie werde ich diesen Screen nicht allzu oft zu sehen bekommen, aber ein bissel herumgeklickt habe ich schon. Resultat: Von allen Programmen dieser Art gefällt mir die Mint-Variante derzeit am besten. Wird dennoch nicht genutzt ;)

Nett, besonders für Neulinge oder Umsteiger, fand ich dieses Feature im Dateimanager, dass mir in dieser Art sonst nur bei OSX über den Weg gelaufen ist:


[![](http://1.bp.blogspot.com/-7kgzL4raaTY/T8dCuzzhQuI/AAAAAAAAAak/cPuFNlU7q30/s320/3.png)](http://1.bp.blogspot.com/-7kgzL4raaTY/T8dCuzzhQuI/AAAAAAAAAak/cPuFNlU7q30/s1600/3.png)


Anwendungen haben hier ein eigenes Lesezeichen und sind übersichtlich wie Apps im Dateimanager angeordnet. Kann mensch so machen, wenn es gefällt, muss aber auch nicht wirklich sein. Dies scheint wohl auch ein Feature zu sein, dass ich weniger nutzen werde, denn mit Kupfer habe ich meinen universellen Programmstarter auf jedem System laufen, das mir unter die Finger kommt.


[![](http://2.bp.blogspot.com/-6sQUl-2FIE4/T8dCzDIw1LI/AAAAAAAAAbE/INJgUtTlYso/s320/5.png)](http://2.bp.blogspot.com/-6sQUl-2FIE4/T8dCzDIw1LI/AAAAAAAAAbE/INJgUtTlYso/s1600/5.png)


Damit sind wir auch mit den Bildern durch. Bleibt nur noch die Gesamteinschätzung.

MintPPC ist schnell. Zwar nicht im Vergleich mit einem LXDE-GNU/Linux-System auf einem Intel Core i7 -- da würde mensch ja wirklich Apfel mit Birnen vergleichen -- aber im Vergleich mit Debian Squeeze, welches gestern morgen noch auf dem Laptop lief. Das OS reagiert in Anbetracht des Alters der Hardware flott und die Programmladezeiten sind ungefähr so lang wie damals, als der Rechner noch neu war. Kurzum: Es macht Spaß mit dieser Hard- und Software zu arbeiten! MintPPC macht Rechner, die eigentlich schon längst abgeschrieben waren, wieder nutzbar ohne dass mensch sich vorkommt als wäre er aus dem letzten Jahrtausend. Was ist mehr zu Erwarten von einem OS, welches "leicht, schlank und schnell" sein möchte?
