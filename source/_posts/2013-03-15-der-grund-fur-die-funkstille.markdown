---
comments: true
date: 2013-03-15 08:29:04
layout: post
slug: der-grund-fur-die-funkstille
title: Der Grund für die Funkstille
wordpress_id: 660
categories:
- Aktiv werden
- In eigener Sache
tags:
- Ampache
- Google
- Ikiwiki
- Owncloud
- Privacy
- Raspberry Pi
- Server
- Soziale Netzwerke
---

Es ist die Woche der schlechten Nachrichten in der IT-Welt. Zwar ist keine wirkliche Hiobsbotschaft von apokalyptischen Ausmaß dabei, aber die Nachrichten reichten aus, um mich zu einigen Änderungen zu bewegen. Ausgerüstet mit einem Raspberry Pi, einer Fritzbox und einem DSL16.000 Anschluss habe ich begonnen, mich von den großen Anbietern zu emanzipieren. Die Zeit, die dafür nötig war, habe ich von der Zeit abgezweigt, die ich normalerweise für mein Blog aufwende. Das offensichtliche Resultat war hier die Funkstille, dafür kann ich jetzt ssl-geschützt von überall auf meine eigene Cloud zugreifen.

<!-- more -->


## Was ist passiert?


Angefangen hat alles mit [dieser kleinen Meldung](http://www.infoworld.com/d/the-industry-standard/when-your-data-not-your-data-when-its-in-the-cloud-213988), die [fefe auf seinem Blog](http://blog.fefe.de/) verlinkt hat. Klar, Kinderpornografie ist schrecklich und absolut verachtenswert, aber die Art, wie sie hier aufgedeckt wurde, stimmt mich ebenso nachdenklich. In meinen Augen steht das Scannen von privaten Daten auf einer Stufe mit dem unbefugten Eindringen in eine Wohnung. Ohne richterlichen Beschluss und Anfangsverdacht hätten die Daten der Person meiner Meinung nach nicht auf Grund einer "pauschalen und routinemäßigen" Untersuchung gescannt werden dürfen. Orwell und "[Du bist Terrorist](http://www.youtube.com/watch?v=SGD2q2vewzQ)" lassen grüßen.

Dann gibt Google zwei Dingen bekannt. 1. [Ad-Blocker werden nicht mehr für Android im Play-Store angeboten](http://stonedgolem.de/?p=657). 2. [Der Google Reader wird eingestellt](http://www.heise.de/newsticker/meldung/Kommentar-Reader-Einstellung-zerstoert-Vertrauen-in-Google-1822798.html). Zu Punkt 1 habe ich mich ja schon geäußert, zu Punkt 2, insbesondere zu dem verlinkten Artikel muss ich aber noch ein paar Worte verlieren, weil der Autor einfach knuffig ist. Wer den Artikel nicht gelesen hat, sollte den nächsten Absatz einfach überspringen.

Der Autor ist drollig. Wie in den Kommentaren schon richtig angemerkt begründet, er sein "Geschäftsmodell Journalismus" auf der Arbeit von Google, ebenso wie Google sein "Geschäftsmodell Reader" auf die Arbeit der RSS-Anbieter aufbaut. Während Google nun dank Leistungsschutzrecht für sein Geschäftsmodell zur Kasse gebeten werden kann, darf der Journalist sich ausheulen, dass ihm sein kostenloser Lutscher weggenommen wird. Seine Konsequenz: "Mir wurde einmal weh getan, deswegen gehe ich dem Leidverursacher komplett aus dem Wege". Zum Beispiel, in dem er sich anstatt eines Android-Tabletts ein Amazon Kindle Fire HD holt. Hmmm ... da war doch was? Ach ja, die Kindle-Dinger laufen auf Android, auch wenn es wegen der vielen Anpassungen nicht mehr so offensichtlich ist. Auch der Wechsel von Chrome zu Firefox ist irgendwie lustig, da Google einer der Hauptfinanzierer von Mozilla ist. Und von Gmail zu Outlook.com zu wechseln ... Nun ja, dazu fällt mir nichts mehr ein. Anstatt also ein über nunmehr Jahre gewachsenes und beständiges Angebot zu nutzen setzt er auf den Neuling, der erstmal beweisen muss, seinen Dienst überhaupt so lange aufrecht zu erhalten wie Google Gmail? Überzeugt mich nicht wirklich.

Abseits der "beleidigte-Leberwurst"-Attitüde des Artikels gibt es eine Aussage, die ich doch unterstützen kann: Sich auf einen Anbieter zu verlassen programmiert Enttäuschungen vor. Entweder, weil ein geliebter Dienst eingestellt wird. Oder weil mit den eigenen Daten schlampig umgegangen wurde. Oder weil sich der Workflow ein wenig veränderte. Oder, oder, oder.


## Gegenmaßnahmen


Es gibt nun einige Möglichkeiten, wie man derartigen Problemen begegnen könnte. Anbieterhopping wäre zwar eine davon, aber sie ist wenig praktikabel. Ständig alles neu eingeben und neu einpflegen? I don't think so.

Eine andere Möglichkeit ist die vielzitierte Hilfe zur Selbsthilfe. Ein wenig Kenntnisse in Linux, einen günstigen Ein-Platinen-Rechner, das eine oder andere Handbuch und die gute alte Internetrecherche gibt die Kontrolle über die eigenen Sachen zurück. Es ist kein Geheimnis, dass ich meinen Raspberry Pi liebe, seit dem ich ihn habe, weil ich jetzt zum ersten Mal einen eigenen Server mit vollem root-Zugriff zur Verfügung habe. In den letzten Tagen habe ich mehr über die Administration von Servern gelernt als ich den zwei Jahren davor, einfach, weil ich selbst etwas zur Hand hatte, das ich im Zweifelsfall kaputtspielen kann. Neben dem reinen Entdeckergeist habe ich auch damit begonnen, mich von einigen Diensten, die ich mehr oder weniger sporadisch nutze, zu trennen.

Dropbox hat es als erstes erwischt, auch wenn es ursprünglich nicht intendiert war. Die Installation und Einrichtung von [Owncloud](https://owncloud.org/) war eher eine Nebenidee, die aufkam, weil ich die benötigte Infrastruktur am Pi zuvor schon wegen anderer Projekte aufgebaut hatte.

Angefangen hatte es mit [Ampache](http://ampache.org/), einen Dienst, der es ermöglicht, Musik vom Webspeicher zu streamen. Ich wollte die Möglichkeit zum Streamen nutzen, um neu aufgenommene Hörspiele direkt über's Tablett und den Rechner abzuhören. Erst wenn mir das Hörspiel gefällt, wollte ich es mit Audacity zurechtschneiden und in meine Sammlung integrieren. Bei Nichtgefallen wollte ich die Aufnahme einfach löschen. Die Folge diese Idee: Ich hatte einen voll funktionsfähigen Webserver auf meinem Pi installiert.

Nachdem ich schon einen vollwertigen HTTP-Server eingerichtet hatte, konnte ich diesen auch nutzen um ein eigenes Wiki zu pflegen, in dem ich Gedanken, Notizen und weiß-der-Teufel-was würde festhalten könnte. Gesagt, gegoggelt, entschieden und getan: Das [Ikiwiki](http://ikiwiki.info/) war schnell aufgesetzt und funktionierte im lokalen Netzwerk. Aber was, wenn ich nicht daheim bin? Wenn ich von woanders auf meine Daten zugreifen will? Ein DynDNS-Dienst musste her und da kam mir meine Fritzbox zugute. Mit dem neuen Dienst MyFritz war das dynamische DNS schnell eingerichtet und die Weiterleitung klappt wunderbar.

Damit hatte ich auf struktureller Seite schon aller Voraussetzungen zur Nutzung von Owncloud erfüllt. Es fehlte nur noch ein Speicherstick als Datenträger und die Installation der eigentlichen Cloud-Software. Ade Dropbox, hallo 32 GB eigener Speicher, der du bist für mich zugänglich überall, wo es Internet gibt.

By the way: Wer wie ich viele Ogg Vorbis Dateien hat und nutzt sollte sich nicht auf den Ampache-Dienst von Owncloud verlassen. Dieser erkennt nur MP3s und funktioniert auch ansonsten nicht so gut wie ein echtes Ampache, weswegen ich weiterhin Ampache neben Owncloud betreibe.


## Was kommt?


Owncloud hat mich auf den Geschmack gebracht. Die vergleichsweise einfache Einrichtung gepaart mit dem Gefühl, die eigenen Daten wieder unter Kontrolle zu haben, animiert mich, weitere Experimente zu unternehmen. Derzeit überlege ich, ob ich dank eigenem Server nicht an einem der vielen dezentralen Netzwerken partizipiere. Diaspora*, Friendica, LiberTree und Tent stehen derzeit in der engeren Auswahl als nächstes erprobt zu werden. Wer möchte kann gerne weitere Empfehlungen hinzufügen.

Aus meiner Sicht wichtig ist, dass wir uns wieder bewusst werden, woher das Internet kommt: Nicht die großen und zentralistischen Firmen haben es uns gebracht, sondern Dezentralität und Do-It-Yourself-Einstellungen, gepaart mit einem ordentlichen Schuss Experimentierfreude! Wir sollten diese Stärken nicht "einfach so" aus der Hand geben und unser Internet dem Firmen überlassen. Dazu gehört, das eigene Handeln gelegentlich zu Überdenken und Alternativen auszuprobieren, auch wenn es ein wenig Frickelarbeit erfordert.

Im Endeffekt ist ja auch Stoned Golem aus dieser Überlegung heraus entstanden, denn sonst wäre ich vielleicht nie von Blogger auf eine selbstgehostete Lösung gewechselt. Insofern stellt mein jetziges Handeln nur eine konsequente Fortführung dar.
