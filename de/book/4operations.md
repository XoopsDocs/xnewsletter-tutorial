# 4.0 Benutzeranleitung

#### Grundsätzliche Information

Dieses Modul basiert auf PHPMailer und PHPMailer-BMH 

#### An- und Abmeldung von Newslettern
Sie können für jede einzelne Gruppe festlegen, ob für eine An-, Abmeldung oder Änderung der Newsletterabonnements ein Bestätigungsmail mit Aktivierungsschlüssel nötig ist oder nicht (Verwendung double-opt-in).

#### Erstellen eines Newsletters
Ein Newsletter kann mit jedem im Xoops-Core installierten Texteditor erstellt werden (z.B. TinyMCE). 
Für die Newsletter können verschiedene Templates/Vorlagen  verwendet werden (siehe auch 'Newsletter Templates').
Sie können für jeden Newsletter mehrere Kategorien (=Empfängergruppen) definieren.
Sie können einem Newsletter maximal 5 Anhänge hinzufügen.

Optional können sie auch einen alten Newsletter kopieren und bearbeiten oder neuerlich senden.

Die Art des Texteditors, die erlaubten Dateitypen und die maximale Dateigröße für Anhänge kann in den Moduleinstellungen festgelegt werden.

#### Newsletter Templates
Die Newsletter basieren auf Templates.
Die Templates werden als Datei im Verzeichnis language/{yourlanguage}/templates oder in der Datenbank gespeichert.
Zum Erstellen eines neuen Templates können sie:
- eine neue html-Datei im Verzeichnis language/{yourlanguage}/templates erstellen und die gewünschten Smarty-Variablen einsetzen
- im Adminbereich ein neues Template erstellen und die gewünschten Smarty-Variablen einsetzen

Dieses Modul verwendet XOOPS [Smarty template engine](http://www.smarty.net/) zum Generieren der Newsletter.

Zulässige Smarty-Variablen sind:
- <{$salutation}> oder <{$sex}>: das Anredefeld und das Geschlecht
- <{$firstname}>: Vorname des Newsletterabonnenten
- <{$lastname}>: Familienname des Newsletterabonnenten
- <{$email}> or <{$subscr_email}>: Email des Newsletterabonnenten
- <{$title}>: Newslettertitel
- <{$content}>: Newsletterinhalt
- <{$date}>: das Sendedatum als timestamp integer<br> 
  (z.B.: <{$date|date_format:"%Y/%m/%d"}> gibt ein formatiertes Datum 2001/01/04 aus)
- <{$unsubscribe_url}>: die Url zur Newsletterabmeldung
- <{$xoops_url}>: die Url der aktuellen Webseite (z.B. http://mydomain.com/)
- <{$xoops_langcode}>: den Sprachencode der aktuellen Seite (z.B. de)
- <{$xoops_charset}>: die Art des Zeichensatzes der aktuellen Seite (z.B. UTF-8)

#### Newsletter senden
Sie können sich vor dem Senden eine Vorschau anzeigen lassen.
Sie können den Newsletter auch zu Testzwecken an eine definierte E-Mail-Adresse senden.
Der Newsletter wird je Abonnent versendet.
Für jede Sendeaktion wird ein Protokolleintrag erstellt. 
Wenn das Senden bei einem oder mehreren Abonnenten fehlgeschlagen ist, können sie dies aus dem Protokoll ersehen.
Sie können den Sendeprozess auch erneut starten. Sie können dabei den Newsletter erneut an alle senden oder nur mehr an jene, bei denen der Sendeprozess fehlgeschlagen ist.

Sie können alle Emails auf einmal oder paketweise versenden.
Das Limit der Pakete und die Anzahl der Minuten bis zum nächsten Sendevorgang können in den Moduleinstellungen festgelegt werden (z.B. 200 Emails alle 60 Minuten).
Das erste Paket wird sofort versendet. Zum Starten der nächsten Sendevorgänge benötigen sie einen externen Cronjob, welcher die Datei "../modules/xnewsletter/cron.php" aufruft. Xoops selbst kann derzeit keine Cronjobs abarbeiten (Version 2.5.5).

Bitte beachten sie: Funktionen wie das Testen der Email-Konten, das Senden von Mails, das Starten des Bounced email handler,... funktionieren nicht mit einem lokalen Server (sie erhalten weiße Seiten).

#### Aufgabenliste
Wenn sie die Emails paketweise versenden, können sie hier sehen, welche Mails auf den nächsten Cronjob warten und die Zeit, an dem der Sendevorgang gestartet werden kann.
Wenn sie die Option "paketweise Versenden" nicht verwenden, ist das Registerblatt "Aufgabenliste" nicht sichtbar.

#### Verwaltung von Mailinglisten
Wenn sie bestehende Mailinglisten verwenden, können sie die An- bzw. Abmeldungen einer Newsletterkategorie mit einer Mailingliste syncronisieren.
Ich verwende neben xNewsletter auch majordomo, damit ich im Bedarfsfall auch von einem normalen EMail-Client aus einen Newsletter an alle Abonnenten schicken kann.
Einer der Nachteile von Mailinglisten ist, dass, sofern jemand bei zwei oder mehr Mailinglisten registriert ist, und ich einen Newsletter an alle Mailinglisten versende, diese Person den gleichen Newsletter mehrfach erhält. Mit xNewsletter erhält er diesen Newsletter nur einmal.

Das Registerblatt "Mailinglisten" ist nicht sichtbar, wenn diese Option deaktiviert ist.

>![](../assets/info/important.png) **ACHTUNG:** xNewsletter kann keine Mailinglisten erstellen 

#### Bounced email handler (BMH)
Wenn Sie Newsletter versenden, wird es immer wieder vorkommen, dass einzelne Mails nicht zugestellt werden können (bounced mails), weil z.B. die E-Mail-Adresse nicht mehr gültig ist, weil die Mailbox voll ist, usw.
Um solche Ereignisse zu verarbeiten und auch darauf zu reagieren, können Sie den BMH verwenden. Sie können den BMH für jedes einzelne E-Mail-Konto aktivieren.
Nicht zustellbare Mails, die vom BMH als solche erkannt werden, können gelöscht oder in einen dafür vorgesehenen Ordner verschoben werden.
Mögliche Aktionen für nicht zugestellte Mails:
-- Keine Aktion (nur Ablage)
-- Vorübergehendes Stilllegen der Anmeldungen für die jeweilige E-Mail-Adresse
-- Löschen der Anmeldungen für die jeweilige E-Mail-Adresse

#### Wartung
Das Modul hat Wartungsfunktionen, welche verschiedene Fehler in der Datenbasis bereinigen können.

#### Import
Sie können die Daten von anderen Newslettermodulen mit diversen Plug-Ins importieren.