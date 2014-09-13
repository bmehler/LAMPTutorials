LAMPTutorials: Installation von MySql 5.6 auf Ubuntu 14.04 Trusty Tahr
======================================================================

Im Zuge meiner Vorbereitung auf die MySQL-Developer 5.6 Zertifizierung, möchte ich hier erklären wie man auf einem Ubuntu 14.04 die MySQL 5.6 Community Server Version installieren kann.

Vorab möchte ich darauf hinweisen, dass bei mir die Installation über sudo apt-get install mysql-server-5.6 mysql-client-5.6 nicht funktionierte. Hierbei brach die Installation wie folgt ab:

*2014-04-21 11:50:07 0 [Warning] Using unique option prefix key_buffer instead of key_buffer_size is deprecated and will be removed in a future release. Please use the full name instead.*

*2014-04-21 11:50:07 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).*

Ich überlegte wie ich auf meinem Ubuntu 14.04 MySQL 5.6 installieren könnte.  Eventuell gibt es ja eine Installatonsanleitung auf der MySQL Website. E voila hier der Link: http://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/

Schritt 1: Download des MySQL Apt Repositories
----------------------------------------------
Das MySQL Apt Repository kann für verschiedene Betriebssystem auf der folgenden Seite herunterladen:

http://dev.mysql.com/downloads/repo/apt/ - der erste Link trifft für Ubuntu 14.04 zu

Da ich auf einer Vagrant Umgebung arbeite, habe ich mir das Repositoy über folgenden Link geladen:

`sudo wget -O mysql.deb http://dev.mysql.com/get/mysql-apt-config_0.2.1-1ubuntu14.04_all.deb`

Schritt 2: Das Repository installieren und updaten
--------------------------------------------------

`sudo dpkg -i mysql.deb`

`sudo apt-get update`

Schritt 3: MySQL 5.6 installieren
---------------------------------

`sudo apt-get install mysql-server`

Während der Installation wird man nach der Version gefragt (5.6/5.7) und man muss das Root-Passwort setzen.

Schritt 4: Mit MySQL (Command-line) arbeiten
--------------------------------------------
Damit man Tabellen anlegen, ändern usw. kann, muss man zuerst nachsehen, ob der MySQL Server läuft. Dies kann man mit dem Befehl: `service mysql status` überprüfen. Analog hierzu kann ma mit `service mysql stop` den Server stoppen, bzw. mit `service mysql restart` den Server neustarten.
Wenn der MySQL Server nun läuft, gibt man im Terminal nach dem Prompt folgendes ein:

`shell> mysql -u root -p bzw. mysql -u root -peuerpassword` (ohne Leer direkt hinter dem p)

Im ersten Fall, wird man nach dem Passwort gefragt (dieses hat ihr während der Installation eingegeben)

Und schon erscheint das Command-line Tool von MySQL.

Nun kann mah z. B. mit `show databases;` die aktuellen Datenbanken anzeigen.
Mit `use database databasename;` (z. B. user) kann man eine Datenbank auswählen und sich mit `show tables;` die Tabellen dieser Datenbank anzeigen lassen. 

Nun setzt ihr ein SQL-Statement ab, welches z. B. so aussehen könnte `SELECT * FROM user where host = 'localhost'\G;`. Das \G steht hier für die formatierte Ausgabe.

Ich wünsche euch viel Spass mit MySQL 5.6 und bedanke mich für eure Aufmerksamkeit.
