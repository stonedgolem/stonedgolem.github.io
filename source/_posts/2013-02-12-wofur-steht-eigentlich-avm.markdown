---
comments: true
date: 2013-02-12 13:13:35
layout: post
slug: wofur-steht-eigentlich-avm
title: Wofür steht eigentlich avm?
wordpress_id: 558
categories:
- Fail
- Zitat des Tages
tags:
- Ärger
- avm
- DAU
- Entfremdung
- Fritzbox
- Simplifizierung
- Technik
---

> "Aktiviere doch einfach mal unter _System -> Ansicht_ die _Expertenansicht_!"




([Forumsbeitrag von RudatNet auf http://www.ip-phone-forum.de vom 18.03.2007](http://www.ip-phone-forum.de/showthread.php?t=131703).)




<!-- more -->


Kaum habe ich die neue Kategorie begonnen, die tägliches Posten erfordert, schon schaffe ich es nicht, mich an dieses Versprechen zu halten. Klar habe ich darüber nachgedacht ein paar "Notfallzitate" bereitzuhalten, die ich nur noch veröffentlichen muss. Aber eine Idee zu zu haben und eine Idee umzusetzen sind zwei Paar Schuhe...

Der Grund für den Ausfall spiegelt sich im heutigen Zitat wider, das schlussendlich das Problem eines Bekannten löste, an dem ich schon seid einiger Zeit tüftelte. Bei diesem Kollegen ist die alte Fritzbox von avm über den Jordan gewandert und sein Provider hat ihm eine neue zugesendet. Zusammen mit allen Passwörtern und Zugangsinformationen, die er brauchte. DSL einzurichten war auch kein Problem, aber die neue Fritzbox wollte sich partout nicht mit dem VOIP-Server verbinden, über den der Bekannte sein Festnetz bekommt.

Ich muss gestehen, von Voice over IP habe ich genau Null Ahnung, wenn es mehr als Skype erfordert -- und bei dem Programm bin ich mir nicht mal sicher, ob es eigentlich das macht, was sich hinter dem Terminus Technicus "VOIP" verbirgt oder ob das nicht doch eine andere Technik ist. Wie dem auch sei, ich persönlich finde es seltsam, eine Telefonleitung für den Datentransfer umzufunktionieren, um datenbasiert via IP wieder dann die Funktion zu realisieren, für die die Leitung ursprünglich entwickelt wurde. Aber soll ja jeder, wie er oder sie will.

Ich schlage mich jedenfalls mehrere Stunden mit der Einstellung dieses VOIP-Services rum und bekomme immer wieder das selber Ergebnis: Verbindung nicht möglich, DNS-Fehler. Aha, okay, der Router findet die Gegenstelle nicht. Da wird sich sicher bei Google was finden, denn ich bin sicher nicht der Erste mit diesem Problem. Ein naiver Gedanke, der eine mehrstündige Suchmaschinenorgie einleitete. Denn: Die Fehlermeldung mit Hinweis auf DNS deutet auf falsche eingegebene Zugangsdaten hin. Jede/r kann sich mal vertippen, aber nicht die gefühlten 30zig Mal, die ich es versucht habe und die ausnahmslos mit dem selben Ergebnis endeten.

Eine Sache hat mich aber von Anfang an stutzig gemacht: Auf dem Schreiben mit den Zugangsdaten gab es noch eine Zeile für einen "Outbound Proxy". Ich hätte meinen Gefühl folgen sollen, anstatt stur auf die Einrichtungsempfehlungen von Provider und avm zu hören. Auch wenn sich beide Quellen einig waren, dass ich nur den Aufforderungen des Einrichtungsassistenten zu folgen habe um das gelobte Land zu erreichen, führte mich dieser Weg dennoch beharrlich in die Wüste. So einfach scheint es wohl doch nicht zu sein, auch wenn ich dem Papier nach alles richtig gemacht habe. Eigenständige Nachforschungen zum Thema Proxys und VOIP brachten mich auch nicht weiter. Zwar gibt im entsprechenden Menü zur Konfiguration der Internettelefonie einen Reiter "Erweiterte Einstellungen", aber da könnte ich lediglich die Länderkennung und die örtliche Vorwahl einstellen. Mehr nicht.

Ergo: Zurück zu Google, denn der Fehler muss irgendwo anders liegen. Viele Foreneinträge mit ähnlicher bis gleicher Problemstellung habe ich gefunden, teilweise sogar den selben Netzanbieter des Kollegen betreffend . Den wenigsten Fragesteller*innen konnte geholfen werden und andere haben sich selbst geholfen, indem sie ihr VOIP über eine andere Lösung als die entsprechende Fritzbox realisiert haben. Beides keine Wege, die mir in dieser Situation gangbar erschienen. Folglich googlte ich weiter. Und Weiter. Und Weiter.

Und STOP.

Besagtes Zitat oben habe ich als Antwort auf eine Frage gefunden, die meinen Anforderungen sehr ähnelte: Der Fragesteller konnte auch keinen "Outbound Proxy" konfigurieren, weil das entsprechende Feld nicht vorhanden war -- so wie bei mir und vielen, vielen anderen Nutzer*innen ebenfalls. Was fehlte war also ein kleiner Haken in einem exotischen Untermenü, welches ich bis dahin nicht mal mit Arsch angeschaut haben bzw. in dem ich überhaupt niemals die Problemlösung vermutet hätte.

Mal im Ernst: Wollt ihr ich verarschen?

Die Eingaben zum "Outbound Proxy" (oder "Proxy Server") wurden ausgeblendet, weil der User schließlich das dümmste anzunehmende Wesen auf diesem Planeten ist, dem man nichts, aber auch gar nichts zuzutrauen ist. Und bevor diese dümmliche Person noch etwas kaputtmacht, geben wir ihr auch keine Möglichkeit an die Hand, um den Service so zu konfigurieren, damit dieser _überhaupt _funktioniert! Diese Tendenz zur Simplifizierung führt doch zwangsweise dazu, dass wir uns immer weniger mit der Technik auseinander setzen und uns dann auf andere verlassen, damit etwas funktioniert. Und dann passiert sowas: In einem abgelegenen Menü fehlt ein Haken -- und weder Hotlinemitarbeiter noch die FAQ von avm noch erfahrene Fritzbox-Nutzer kommen bei der Fehlermeldung "DNS-Problem" auf die Idee, dass dieses Häkchen aktiviert werden sollte, damit ein Proxy konfiguriert werden kann -- vor allem, wenn es im eigentlichen Menü einen Reiter mit "erweiterten Einstellungen" gibt, hinter denen ich die "Spezialeinstellungen" intuitiv vermuten würde! Hätte es von Anfang an die Möglichkeit gegeben den Proxy einzugeben, dann hätte ich meinen gestrigen Nachmittag mit etwas sinnigeren verbringen können. Aber so: Pustekuchen.

Also, liebe Hersteller und Herstellerinnen und Hersteller*, wir, die Nutzer*innen, sind nicht so dumm, wie ihr denkt. Aber wenn Optionen ausgeblendet werden, die auch nur im _Entferntesten relevant _sein könnten, dann will ich darüber auch _auf der Seite _informiert werden! Und wenn es einen Reiter für weitere Einstellungen gibt, dann erwarte ich davon, dass sich hinter diesen die "Experteneinstellungen" verstecken. Aber welcher normal denkende Menschen kommt darauf, dass es unter "Ansicht" nochmal eine Option zum Freischalten der "Experteneinstellungen" gibt?!

Danke avm, für mehrere Stunden, die ich sinnlos mit Googlen verbringen durfte, nur weil ihr mich für dümmer haltet und gleichseitig dümmer macht, als ich es bin. Wahrlich, eine Glanzleistung!
