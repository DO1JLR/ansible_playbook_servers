 Mailserver Setup
========================
Das Mailserver Setup wurde inspiriert von [thomas-leister.de/mailserver-debian-buster/](https://thomas-leister.de/mailserver-debian-buster/).

 Hintergrundwissen
------------------

**Dovecot**

Dovecot ist ein weit verbreiteter MDA (Mail Delivery Agent) und IMAP-Server. Er sortiert ankommende E-Mails in die Postfächer des jeweiligen Empfängers ein und stellt eine Schnittstelle zum Abrufen der Mailbox bereit (IMAP). Außerdem wird Dovecot in diesem Setup von Postfix als sog. SASL-Authentifizierungsserver genutzt: Postfix fragt Dovecot, ob ein bestimmter Benutzer berechtigt ist, sich am System anzumelden.

**Postfix**

Postfix wird oft zusammen mit Dovecot eingesetzt. Der populäre MTA (Mail Transfer Agent) kümmert sich um alles, was mit dem Transport der E-Mail zu tun hat: Vom E-Mail Client zum eigenen Mailserver, und von dort aus zum jeweiligen Zielserver. Außerdem nimmt Postfix E-Mails von fremden Servern an und leitet sie an den MDA Dovecot weiter. Antispam-Software wird i.d.R. direkt in Postfix integriert, um eintreffende Spammails erst gar nicht in die Mailbox des Nutzers gelangen zu lassen.

Anmerkung: Postfix ist “der eigentliche Mailserver”. E-Mails können ohne weiteres einzig und allein mit Postfix gesendet und empfangen werden. Alle weiteren Komponenten wie Dovecot und Rspamd machen uns das Leben allerdings einfacher ;-)
MariaDB (MySQL-Datenbank)

Dovecot und Postfix werden so konfiguriert, dass sie eine MySQL-Datenbank als Backend (Datenbasis) nutzen. In der Datenbank werden zu nutzende Domains, Benutzer, Aliase und weitere Daten gespeichert. Durch einfaches Hinzufügen oder Entfernen von Datensätzen in oder aus Datenbanktabellen können neue Benutzer oder Aliase angelegt oder gelöscht werden. Der Vorteil eines Datenbank-Backends ist, dass sich der Mailserver damit sehr einfach verwalten lässt: So ließe sich zur Benutzerverwaltung beispielsweise eine Weboberfläche in PHP entwickeln, die die MySQL-Datenbank verändert. Die Serverkonfiguration muss dann nicht manuell geändert werden.

**Rspamd**

Rspamd ist ein Filtersystem, das in Postfix integriert wird und eingehende E-Mails überprüft. Spammails werden von Rspamd erkannt und nicht an den Benutzer zugestellt bzw. aussortiert. Außerdem fügt Rspamd bei ausgehenden E-Mails eine DKIM-Signatur hinzu, sodass fremde Mailserver eigene Mails nicht als verdächtig einstufen.

**Nginx**

Nginx ist ein weit verbreiteter und schlanker Webserver / Webproxy. In diesem Setup hat er mehrere Aufgaben: Zum einen kann er als Endpunkt für den Ausstellungsprozess von Let’s Encrypt-Zertifikaten dienen, zum anderen als Proxy für die Rspamd-Weboberfläche, oder um die Autokonfigurationsdatei für Mailclients anzubieten.

**Redis**

Redis ist ein hochperformanter In-memory Key-Value-Store, also eine sehr einfache, schnelle Datenbank, welche Schlüssel-Wert-Paare effizient im Speicher ablegen kann. Rspamd nutzt Redis, um einige Daten zwischenzuspeichern (wie z.B. zuletzt überprüfte Mailserver).
