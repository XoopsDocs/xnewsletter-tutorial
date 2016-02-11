# 3.0 Moduleinstellungen

In den Moduleinstellungen können sie verschiedene Optionen für dieses Modul bearbeiten:<br/>

![](../assets/preferences_de.PNG)

## Optionen im Detail
#### Editor
Legen sie fest, welcher Editor auf der Benutzerseite für die Erstellung eines Newsletters verwendet werden soll.

#### Schlüsselwörter
Sie können Schlüsselwörter definieren, die den Meta Tags hinzugefügt werden. Separieren sie die Schlüsselwörter mit einem Komma.

#### Maximale Dateigröße
Bitte definieren sie die maximale Dateigröße für Newsletter-Anhänge. Geben sie den Wert für Bytes an (10485760 = 1 MB).

#### Mime-Types
Bitte definieren sie die erlaubten Dateitypen für Define Newsletter-Anhänge.

#### Upload Pfad
Bitte definieren sie den Ordner, in dem Newsletter-Anhänge gespeichert werden sollen ( Ordnder in {XOOPS_ROOT_PATH}/uploads ), mit Schrägstrich am Anfang und am Ende.<br/>
>**Achtung:** vergewissern sie sich, dass dieser Pfad wirklich existiert, - xnewsletter erstellt keine Pfade/Ordner

#### Anzahl Listeneinträge bei Admin-Seiten
Definieren sie die Anzahl der Listeneinträge pro Seite.
	
#### Werbecode
Bitte hier Code für Werbungen eingeben.
	
#### Anzeige Social Networks?
Wenn die Buttons für Social networks angezeigt werden sollen, dann bitte "Ja" wählen

#### Code für Schaltflächen für Soziale Netzwerke
Bitte Code für Social Networks eingeben
	
#### Verwende Zusatzfeature Mailinglisten
Wenn sie bestehende Mailinglisten verwenden wollen, können sie diese mit den Abonnenten von Newsletterkategorien syncronisieren lassen.<br/>Wenn sie diese Funktion aktivieren, wird ihnen im xnewsletter-Admin-Bereich ein zusätzliches Registerblatt angezeigt.
>![](../assets/info/important.png) **ACHTUNG:** xnewsletter kann keine Mailinglisten erstellen. 

#### Feld 'Anrede' verwenden
Bitte entscheiden sie, ob eine Anrede (wie z.B. "Herr", "Frau",...) verwendet werden soll.

#### Gruppen mit An-/Abmeldung ohne Bestätigungsmail
Definieren sie die Gruppen, welche eine An- oder Abmeldung für einen Newsletter direkt durchführen darf (ohne Senden eines Bestätigungsmails)

#### Gruppen mit der Berechtigung zum Ändern von An-/Abmeldungen
Bestimmen Sie bitte die Gruppen, die An-/Abmeldungen von anderen Personen bearbeiten dürfen. Ein Löschen der Registrierung ist nicht möglich. Diese Gruppen müssen auch die Berechtigung zum Auflisten der Abonnenten zu einer Newsletterkategorie haben. Diese Gruppen sollten außerdem die Berechtigung zum Erstellen eines Newsletters haben.
	
#### E-Mails paketweise versenden
Anzahl der E-Mails, die in einem Paket gesammelt versendet werden sollen. 0 bedeutet, dass alle E-Mails immer sofort versendet werden. Sie können diese Option nur verwenden, wenn Sie Cronjobs von einem externen Programm aus starten können.
	
#### Zeitspanne für paketweises E-Mail versenden
Zeitspanne in Minuten,bis das nächste Paket versendet werden soll. Wird nur berücksichtigt, wenn 'E-Mails paketweise versenden' größer 0 ist.

