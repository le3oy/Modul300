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
