
Modul 300 LB02

# Modul 300 LB02

_Leonardo Wild_  
Dies ist eine Dokumentation für die LB02 im Modul 300. In dieser Dokumentation soll ich meine Arbeitsschritte festhalten.

## K1 Einrichtung

In diesem Punkt soll die Struktur für die Weitere LB aufgebaut werden. Hierzu waren folgende Programme notwendig:

-   VirtualBox
-   Vagrant 
- Visualstudio-Code
-   Git-Client
-   SSH-Key für Client erstellt

Für die meisten Elemente in dieser Liste bedarf es keiner Erklärung. Den SSH Key habe ich entsprechend der Aufgabe auf Github in den Einstellungen erstellt. Den Git-Client konnte ich auch dort herunterladen.

Mit der Lizenz welche wir von der TBZ zur Verfügung hatten, konnte ich VisualStudio Code installieren.  

VirtualBox war gratis für die Installation auf ihrer Webseite.

Vagrant konnte ich als Add-On zu Git-Hub herunterladen. MIt Vagrant lassen sich VMs einfach über die Git-Bash Konsole erstellen.

Danach habe ich noch einen Linux Ubuntu Client aufgesetzt.  
![enter image description here](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a7/Ubuntu_19.10_Desktop.png/1200px-Ubuntu_19.10_Desktop.png)

**Kannte ich schon:**
Ich kannte schon die Programme Virtual Box und den Git-Client. 

**War neu für mich:**
Das Programm Vagrant und dessen Vorteile kannte ich noch nicht. Auch habe ich einen schnelleren Umgang mit Git-Bash gelernt. Auch habe ich noch nie einen SSH Key über git Bash aufgesetzt.
## K2 Lernumgebung

In diesem Punkt geht es um das registrieren und vorbereiten für die nächsten Aufgaben. Hierzu sollten folgende Punkte erledigt werden.

-   GitHub oder Gitlab-Account ist erstellt
-   Git-Client wurde verwendet
-   Dokumentation ist als Mark Down vorhanden
-   Markdown-Editor ausgewählt und eingerichtet
-   Mark down ist strukturiert
-   Persönlicher Wissenstand im Bezug auf die wichtigsten Themen sind dokumentiert
-   Wichtige Lernschritte sind dokumentiert

Nun zu einigen von diesen Punkten braucht es wieder keine Erklärung. Die Dokumentation wurde als Mark Down angelegt.  
Kommen wir zu einigen Begriffen welche geklärt werden sollten.  
**Linux** ist ein Open Source Betriebssystem. Die Vorteile von Linux liegen darin, dass jeder den Code einsehen und benutzen kann. So können Sicherheitslücken besser geschlossen werden und es kann viel optimiert werden.  
Die **Virtualisierung** soll die Wartung von Arbeitsplätzen oder Servern vereinfachen. Anstelle von Vielen Servern, werden nur weniger eingesetzt. Es wird also weniger Hardware gebraucht. Auf den Servern ist ein Programm für die Virtualisierung installiert. Nun lassen sich auf diesem Server mithilfe der Virtualisierung Virtuele Server, Clients und Netze installieren.  
**Vagrant** ist eine Freie Software für das erstellen von Virtuellen Maschinen. Mit Vagrant lassen sich auch einige Arbeitsschritte automatisieren.  
**Git** ist eine Freeware welche zur Pensionierung und Veröffentlichung/Verteilung von Programmen gebraucht wird.

**Kannte ich schon:** 
Ehrlich gesagt kannte ich zu diesem Punkt sehr wenig. Ich kannte den Git-Client und den umgang damit.

**War neu für mich**
Ich habe vor diesem Project noch nie mit Git-Hub gearbeitet. Ich muss sagen, dass ich gefallen daran gefunden habe. Ich habe einen Editor benutzt namens StackEdit um den Text vorzubereiten. Danach konnte ich einfach alles Kopieren und hier bei Github einsetzen.
## K3 Vagrant

Zu Vagrant habe ich schon im Abschnitt K2 geschrieben.  
Dies sind die Punkte welche ich erfüllen sollte:

-   Bestehende vm aus Vagrant-Cloud einrichten
-   Kennt die Vagrant-Befehle
-   Eingerichtete Umgebung ist dokumentiert (UmgebungsVariablen, Netzwerkplan gezeichnet, Sicherheitsaspekte)
-   Funktionsweise getestet inkl. Dokumentation der Testfälle
-   vorgefertigte vm auf eigenem Notebook aufgesetzt
-   Projekt mit Git und Mark Down dokumentiert

**Netzwerkplan**

Laptop VM Adapter -------------------- Server3 Vagrant VM
   
   10.0.2.2-----------ssh port 22 ------------10.0.2.15
  
**VM aus Cloud einrichten**  
Boxen sind bei Vagrant vorkonfigurierte VMs (Vorlagen). Diese sollen den Prozess der Softwareverteilung und der Entwicklung beschleunigen. Boxen können explizit durch den Befehl `vagrant box add [box-name]` oder `vagrant box add [box-url]` heruntergeladen und durch `vagrant box remove [box-name]` entfernt werden.  
Die Konfiguration findet hier im Vagrant File Statt. In das Vagrant File sollen folgende Zeilen hineingeschrieben werden:

*_Vagrant.configure(“2”) do |config| config.vm.define :apache do |web| web.vm.box = “bento/ubuntu-16.04” web.vm.provision :shell, path: “config\_web.sh” web.vm.hostname = “srv-web” web.vm.network :forwarded\_port, guest: 80, host: 4567 web.vm.network “public_network”, bridge: “en0: WLAN (AirPort)”  
end_

_config.vm.provision :shell, inline: <<-SHELL  
sudo apt-get update sudo apt-get -y install apache2  
SHELL_

_config.vm.provider “virtualbox”  
do |vb| vb.memory = “512”  
end_*

Nun muss eine Box auf dem Lokalem Computer erstellt werden  
`$ vagrant box add [box-name]`

jetzt kann eine VM erstellt werden  
`$ mkdir myserver`  
`$ cd myserver`  
`$ vagrant init ubuntu/xenial64`  
`$ vagrant up`

MIt `vagrant destroy -f` lässt sich die erstellte VM wieder löschen.

**Vagrant Befehle**  
`vagrant init` Initialisiert im aktuellen Verzeichnis eine Vagrant-Umgebung und erstellt, falls nicht vorhanden, ein Vagrantfile

`vagrant up`  
Erzeugt und Konfiguriert eine neue Virtuelle Maschine, basierend auf dem Vagrantfile

`vagrant ssh`  
Baut eine SSH-Verbindung zur gewünschten VM auf

`vagrant status`  
Zeigt den aktuellen Status der VM an

`vagrant port`  
Zeigt die Weitergeleiteten Ports der VM an

`vagrant halt`  
Stoppt die laufende Virtuelle Maschine

`vagrant destroy`  
Stoppt die Virtuelle Maschine und zerstört sie.

**Kannte ich schon:** 
Ich kannte mich gar nicht mit Vagrant aus.

**War neu für mich**
Ich kann nun Virtuelle Mashcienen mit Vagrant erstellen. Ich kann auch anschliessend auf diese drauf Verbinden und sie konfigurieren. Während meiner Arbeitszeit konnte ich die Befehle von Vagrant zu genüge einsetzen, sodass ich sie jetzt gut kenne. 

## K4 Sicherheit
Hier sind wieder die Verlangten Punkte aufgelistet:

-   Firewall eingerichtet inkl. Rules
-   Reverse-Proxy eingerichtet
-   Benutzer- und Rechtevergabe ist eingerichtet (optional)
-   Zugang mit SSH-Tunnel abgesichert
-   Sicherheitsmassnahmen sind dokumentiert
-   Projekt mit Git und Mark Down dokumentiert

**FireWall**
Zuerst habe ich das Programm UFW welches wir für diese Aufgabe verwenden sollten installiert.
`sudo apt-get install ufw`

Mit `sudo ufw status` lässt sich der Status überprüfen. Mit `sudo ufw enable` lässt sich die FireWall einschalten und mit `sudo ufw disable` lässt sie sich deaktivieren.

Danach gilt es die nötigen Ports in der FireWall zu öffnen. Ich habe Port 22 für meinen Laptop freigegeben um weiterhin mit ssh darauf zugreifen zu können.
 `sudo ufw allow from 10.0.2.2 to any port 22`
Danach habe ich noch Port 80 für http freigegeben. 
`sudo ufw allow 80/tcp`

Beim installieren der FireWall ist darauf zu achten, die richtigen Ports für die richtigen IP Adressen freizugeben. So ist es mir passiert, dass ich den Port 22 für die Falsche Adresse freigegeben habe. So konnte ich nicht mehr auf meine VM Zugreifen und mein Fortschritt war dahin.

Zum Testen am Ende kann man einfach `sudo ufw status` eingeben. Die Ausgabe beschriebt auf welchen ports welche Komunikation zugelassen ist. Bei mir sieht dies wie folgt aus:
![enter image description here](https://raw.githubusercontent.com/le3oy/Modul300/master/FireWall.PNG)

Desweiteren kann man noch probieren den host zu pingen. Diese Funktion sollte deaktiviert sein:
![enter image description here](https://raw.githubusercontent.com/le3oy/Modul300/master/Ping.PNG)
**Reverse Proxy**
Zuerst habe ich alle notwendigen Module installiert.
`sudo apt-get install libapache2-mod-proxy-html`
`sudo apt-get install libxml2-dev`
`sudo apt-get install apache 2`

Anschließend habe ich folgende Module aktiviert.
`sudo a2enmod proxy`
`sudo a2enmod proxy_html`
 `sudo a2enmod proxy_http`

Danach habe ich Die Datei /etc/apache2/apache2.conf ergänzt.
`ServerName localhost`

Danach kann der Apache WebServer neu gestartet werden.
`sudo service apache2 restart`

Zum Schluss habe ich dann noch einige Konfigurationen im `001-reverseproxy.conf`File vorgenommen

    # Allgemeine Proxy Einstellungen
    ProxyRequests Off
    <Proxy *>
        Order deny,allow
        Allow from all
    </Proxy>

    # Weiterleitungen master
    ProxyPass /master http://master
    ProxyPassReverse /master http://maste

**Kannte ich schon:** 
Ich kannte mich etwas mit FireWalls auf der Linux umgebung aus. Jedoch habe ich noch nie einen Reverse Proxy konfiguriert.

**War neu für mich**
Ich kann nun eine UFW Firewall aufsetzen und konfigurieren. Ich kann einzelne Ports freigeben. Ich kann einen ReverseProxy einrichten. 
## Schlusswort und Fazit

Zum Schluss gibt es zu sagen, dass ich meine Ziele erfüllen konnte. Auch wenn ich nicht mit allem 100% zufrieden bin und mehr möglich gewesen wäre in dieser Zeit, bin ich mit meinen Leistungen im Unterricht zufrieden. Ich hatte in letzter Zeit etwas Schwierigkeiten im Privaten. Jedoch konnte ich dies endlich mal etwas von meinen Modulen weghalten und während den Stunden konzentriert arbeiten. Ich hätte jedoch noch mehr Zuhause machen können für eine Bessere Note. Ich habe mich aber dafür entschieden mich um andere Dinge zu kümmern. Und nun da ich dies Bewusst gemacht habe, fühle ich mich zufrieden.



Modul 300 LB03

# Modul 300 LB03

_Leonardo Wild_  
Dies ist eine Dokumentation für die LB02 im Modul 300. In dieser Dokumentation soll ich meine Arbeitsschritte festhalten.

## K1 Einrichtung

In diesem Punkt soll die Struktur für die Weitere LB aufgebaut werden. Hierzu waren folgende Programme notwendig:

-   VirtualBox
-   Vagrant 
- Visualstudio-Code
-   Git-Client
-   SSH-Key für Client erstellt

Für die meisten Elemente in dieser Liste bedarf es keiner Erklärung. Den SSH Key habe ich entsprechend der Aufgabe auf Github in den Einstellungen erstellt. Den Git-Client konnte ich auch dort herunterladen.

Mit der Lizenz welche wir von der TBZ zur Verfügung hatten, konnte ich VisualStudio Code installieren.  

VirtualBox war gratis für die Installation auf ihrer Webseite.

Vagrant konnte ich als Add-On zu Git-Hub herunterladen. MIt Vagrant lassen sich VMs einfach über die Git-Bash Konsole erstellen.

Danach habe ich noch einen Linux Ubuntu Client aufgesetzt.  
![enter image description here](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a7/Ubuntu_19.10_Desktop.png/1200px-Ubuntu_19.10_Desktop.png)

**Kannte ich schon:**
Ich kannte schon die Programme Virtual Box und den Git-Client. 

**War neu für mich:**
Das Programm Vagrant und dessen Vorteile kannte ich noch nicht. Auch habe ich einen schnelleren Umgang mit Git-Bash gelernt. Auch habe ich noch nie einen SSH Key über git Bash aufgesetzt.
## K2 Lernumgebung

In diesem Punkt geht es um das registrieren und vorbereiten für die nächsten Aufgaben. Hierzu sollten folgende Punkte erledigt werden.

-   GitHub oder Gitlab-Account ist erstellt
-   Git-Client wurde verwendet
-   Dokumentation ist als Mark Down vorhanden
-   Markdown-Editor ausgewählt und eingerichtet
-   Mark down ist strukturiert
-   Persönlicher Wissenstand im Bezug auf die wichtigsten Themen sind dokumentiert
-   Wichtige Lernschritte sind dokumentiert

Nun zu einigen von diesen Punkten braucht es wieder keine Erklärung. Die Dokumentation wurde als Mark Down angelegt.  
Kommen wir zu einigen Begriffen welche geklärt werden sollten.  
**Linux** ist ein Open Source Betriebssystem. Die Vorteile von Linux liegen darin, dass jeder den Code einsehen und benutzen kann. So können Sicherheitslücken besser geschlossen werden und es kann viel optimiert werden.  
Die **Virtualisierung** soll die Wartung von Arbeitsplätzen oder Servern vereinfachen. Anstelle von Vielen Servern, werden nur weniger eingesetzt. Es wird also weniger Hardware gebraucht. Auf den Servern ist ein Programm für die Virtualisierung installiert. Nun lassen sich auf diesem Server mithilfe der Virtualisierung Virtuele Server, Clients und Netze installieren.  
**Docker** Docker vereinfacht die Bereitstellung von Anwendungen, weil sich Container, die alle nötigen Pakete enthalten, leicht als Dateien transportieren und installieren lassen.  
**Git** ist eine Freeware welche zur Pensionierung und Veröffentlichung/Verteilung von Programmen gebraucht wird.

**Kannte ich schon:** 
Ehrlich gesagt kannte ich zu diesem Punkt sehr wenig. Ich kannte den Git-Client und den umgang damit.

**War neu für mich**
Ich habe vor diesem Project noch nie mit Git-Hub gearbeitet. Ich muss sagen, dass ich gefallen daran gefunden habe. Ich habe einen Editor benutzt namens StackEdit um den Text vorzubereiten. Danach konnte ich einfach alles Kopieren und hier bei Github einsetzen.

## K3 Docker

Dies sind die Punkte welche ich erfüllen sollte:

- Bestehenden Docker-Dontainer kombinieren
- Bestehende Container als Backend, Desktop-App als Frontend
einsetzen
- Volumes zur persistenten Datenablage eingerichtet
- Kennt die Docker spezifischen Befehle
- Eingerichtete Umgebung ist dokumentiert (UmgebungsVariablen, Netzwerkplan gezeichnet, Schichtenmodell,
Sicherheitsaspekte)
- Funktionsweise getestet inkl. Dokumentation der Testfälle
- Projekt mit Git und Markdown dokumentiert

Docker habe ich auf der Ofiziellen Webseite heruntergeladen und bei mir auf dem Client installiert. Anschliessend muss der Computer neu gestartet werden. Wichtig ist es auch noch die Virtualisierung im BIOS einzustellen. Ansonsten wird Docker nicht starten. Wenn alles installiert ist, lässt sich auf Docker über CMD zugreifen.   

**Docker Befehle**  
Standard-Test:

    $ docker run hello-world
Startet einen Container mit einer interaktiven Shell (interactive, tty):

    $ docker run -it ubuntu /bin/bash
Startet einen Container, der im Hintergrund (detach) läuft:

    $ docker run -d ubuntu sleep 20
Startet einen Container im Hintergrund und löscht (remove) diesen nach Beendigung des Jobs:

    $ docker run -d --rm ubuntu sleep 20
Startet einen Container im Hintergrund und legt eine Datei an:

    $ docker run -d ubuntu touch /tmp/lock
Startet einen Container im Hintergrund und gibt das ROOT-Verzeichnis (/) nach STDOUT aus:

    $ docker run -d ubuntu ls -l

    $ docker ps
Aktive und beendete Container anzeigen (all):

    $ docker ps -a
Nur IDs ausgeben (all, quit):

    $ docker ps -a -q

Lokale Images ausgeben:
    $ docker images

    $ docker image ls
docker rm und docker rmi

    $ docker rm [name]
Alle beendeten Container löschen:

    $ docker rm `docker ps -a -q`
Alle Container, auch aktive, löschen:

    $ docker rm -f `docker ps -a -q`
Docker Image löschen:

    $ docker rmi ubuntu
Zwischenimages löschen (haben keinen Namen):

    $ docker rmi `docker images -q -f dangling=true`

    $ docker start`
Startet einen (oder mehrere) gestoppte Container.

Docker Container neu starten, die Daten bleiben erhalten:

    $ docker start [id]

Container stoppen, killen
    `$ docker stop`
  
Stoppt einen oder mehrere Container (ohne sie zu entfernen). Nach dem Aufruf von docker stop für einen Container wird er in den Status »exited« überführt.
     `$ docker kill`
Schickt ein Signal an den Hauptprozess (PID 1) in einem Container. Standardmässig wird SIGKILL gesendet, womit der Container sofort stoppt.

Informationen zu Containern

   `$ docker logs`
Gibt die "Logs" für einen Container aus. Dabei handelt es sich einfach um alles, was innerhalb des Containers nach STDERR oder STDOUT geschrieben wurde.
   `$ docker inspect`
Gibt umfangreiche Informationen zu Containern oder Images aus. Dazu gehören die meisten Konfigurationsoptionen und Netzwerkeinstellungen sowie Volumes-Mappings.
   `$ docker diff`
Gibt die Änderungen am Dateisystem des Containers verglichen mit dem Image aus, aus dem er gestartet wurde.
   `$ docker top`
Gibt Informationen zu den laufenden Prozessen in einem angegebenen Container aus.

**MYSQL über Docker**

Zuerst habe ich eine MYSQL VM angelegt:
`$ docker run --rm -d --name mysql mysql`
Um zu überprüfen ob die Container angelegt wurden, lässt sich der Comand `Docker ps` gebrauchen.

Danach habe ich die internet VErbindung sichergestellt:
MySQL Container permanent an Host Port 3306 weiterleiten:
`$ docker run --rm -d -p 3306:3306 mysql`

**Image Bereitstellung**
Imagenamen und -Tags werden beim Bauen der Images oder durch den Befehl docker tag gesetzt:

    $ docker build -t mysql .
    $ docker build -t mysql:1.0 .
    $ docker tag mysql username/mysql
    
*Docker Hub einrichten*
1. Acount auf Docker Hub eröffnen. (Name: le3oy)
2. Imagenamen mit Usernamen, laut Account auf Docker Hub, taggen:
    `$ docker tag mysql username/mysql`
3. Image hochladen:
    `$ docker push username/mysql`
4. Dashboard auf Docker Hub anwählen und Image beschreiben.
5. Auf dem Client über CMD mit dem Docker Account anmelden.
     `$ docker login`

Container können mittels docker export und docker import und Images mittels docker save und docker load von/nach Verzeichnisse kopiert werden.

**Kannte ich schon:** 
Ich kannte mich in dem ganzen Thema noch wenig aus.

**War neu für mich**
Ich weis nun wie ich über Docker VMs erstellen und konfigurieren kann.

## K4 Sicherheit
Dies sind die Punkte welche ich erfüllen sollte:

Sicherheitsaspekte sind implementiert
- Service-Überwachung ist eingerichtet
- Aktive Benachrichtigung ist eingerichtet
- mind. 3 Aspekte der Container-Absicherung sind berücksichtigt
- Sicherheitsmassnahmen sind dokumentiert (Bezug zur eingerichteten Umgebung ist vorhanden)
- Projekt mit Git und Markdown dokumentier

**Login**
Mit folgenden Daten lassen sich die Login Daten kontrollieren.

Standard-Logging (JSON-File)
Einfache Ausgaben abholen:

    $ docker run --name logtest ubuntu bash -c 'echo "stdout"; echo "stderr" >>2'
    $ docker logs logtest
    $ docker rm logtest
Laufende Ausgaben anzeigen:

    $ docker run -d --name streamtest ubuntu bash -c 'while true; do echo "tick"; sleep 1; done;'
    $ docker logs streamtest 
    $ docker logs streamtest | wc -l
    $ docker rm streamtest

Protokollierung in das System-Log (syslog) des Hosts:

    $ docker run -d --log-driver=syslog ubuntu bash -c 'i=0; while true; do i=$((i+1)); echo "docker $i"; sleep 1; done;'
    $ tail -f /var/log/syslog
    
**Absichern**
Zu den wichtigsten Dingen, um einen Container abzusichern, gehören:

-Die Container laufen in einer VM oder auf einem dedizierten Host, um zu vermeiden, dass andere Benutzer oder Services angegriffen -werden können.
-Der Load Balancer / Reverse-Proxy ist der einzige Container, der einen Port nach aussen freigibt, wodurch viel Angriffsfläche verschwindet. Monitoring oder Logging-Services sollten über private Schnittstellen oder VPN nutzbar sein.
-Alle Images definieren einen Benutzer und laufen nicht als root.
-Alle Images werden über den eigenen Hash heruntergeladen oder auf anderem Wege sicher erhalten und verifiziert.
-Die Anwendung wird überwacht und es wird Alarm ausgelöst, wenn eine ungewöhnliche Netzwerklast oder auffällige Zugriffsmuster erkannt werden.
-Alle Container laufen mit aktueller Software und im Produktivmodus – Debug-Informationen sind abgeschaltet.
-AppArmor oder SELinux sind auf dem Host aktiviert
-Services wie z.B. Apache, Mysql ist mir irgendeiner Form der Zugriffskontrolle oder einem Passwortschutz ausgestattet.

Weitere Massnahmen:
-Unnötige setuid-Binaries werden aus den identidock-Images entfernt. Damit verringert sich das Risiko, dass Angreifer, die Zugriff auf einen Container erhalten haben, ihre Berechtigungen erweitern können.
-Dateisysteme werden so weit wie möglich schreibgeschützt eingesetzt.
-Nicht benötigte Kernel-Berechtigungen werden so weit wie möglich entfernt.    

**Weitere Sicherheitstipps**

User setzen
   `$ RUN groupadd -r user_grp && useradd -r -g user_grp user
    $ USER user`

setuid/setgid-Binaries entfernen
   `$ FROM ubuntu:14.04`
    `$ RUN find / -perm +6000 -type f -exec chmod a-s {} \; || true`


Speicher begrenzen
     `$ docker run -m 128m --memory-swap 128m amouat/stress stress --vm 1 --vm-bytes 127m -t 5s`
     
CPU-Einsatz beschränken
   `$ docker run -d --name load1 -c 2048 amouat/stress
    $ docker run -d --name load2 amouat/stress
    $ docker run -d --name load3 -c 512 amouat/stress
    $ docker run -d --name load4 -c 512 amouat/stress
    $ docker stats $(docker inspect -f {{.Name}} $(docker ps -q))`
    
Zugriffe auf die Dateisysteme begrenzen
   `$ docker run --read-only ubuntu touch x`
   
Capabilities einschränken
   `$ docker run --cap-drop all --cap-add CHOWN ubuntu chown 100 /tmp`
    
##Reflexion
Dieses Projekt hat mir viel mühe bereitet und hat in einer turbulenten Zeit meines lebens statgefunden. Ich habe aber trotzdem probiert einfachere Aufgaben umzusetzen und meinen Teil aus der Aufgabe zu lernen und hier festzuhalten. Ich habe probiert das Projekt so zu Dokumentieren, dass ich es nochmals nachbauen kann. Ich denke dies ist mir gut gelungen. Ich hätte aber mehr Zeit und begeisterung ins Projekt stecken können. Es wäre sicher noch Einiges möglich gewesen. 
