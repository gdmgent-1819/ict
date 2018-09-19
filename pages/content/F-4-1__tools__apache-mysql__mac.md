---
layout   : course
permalink: tools/apache-mysql/mac/
published: false
#
title     : macOS
title_long: Apache-installatie op macOS Sierra
---

Inleiding
---------

> Ingebouwde ontwikkelomgeving
> ----------------------------
> Er zijn veel mogelijkheden om ontwikkelomgevingen op te zetten, waaronder het populaire MAMP en MAMP Pro dat een handige User Interface heeft bovenop de Apache, PHP en MySQL laag. Hier ben je echter beperkt in configuratie waar wij als pro developers (to be) wel nood aan hebben.
{:.card.card-definition}

Deze EHBI cursus heeft wel enkele *randvoorwaarden*

- OS: laatste versie van Mac OS X (Sierra Versie: 10.12.6)
- Xcode: Installeer Xcode via de App Store
- Xcode CLI: Installeer ook de Command Line Tools via de terminal met commando:  
`sudo xcode-select --install`

Installatie van Homebrew
------------------------
Homebrew is een OSX Package Manager. Via `brew` kan je gemakkelijk sterke functionaliteit toevoegen aan je Mac. Echter we moeten de package manager er wel nog op installeren. Open de Terminal en geef commando in:  
{% highlight bash %}
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
{% endhighlight %}

Volg de instructies op en geef je wachtwoord in waar nodig. Als de installatie voltooid is, is het een 'good practice' om ook even na te kijken of alles correct geconfigureerd is: 

Er zullen instructies verschijnen als er nog extra ingrepen nodig zijn.  
{% highlight bash %}
$ brew doctor
{% endhighlight %}
PS, het dollarteken goef je niet mee te kopiëren


### Extra brew taps

Wij hebben nog enkele 'extensies' nodig, taps genaamd.
{% highlight bash %}
$ brew tap homebrew/dupes
$ brew tap homebrew/versions
$ brew tap homebrew/php 
$ brew tap homebrew/apache
{% endhighlight %}


### Update brew 
{% highlight bash %} 
$ brew update
{% endhighlight %}

Apache Installatie
------------------

Op de meest recente OS van Mac staat standaard reeds Apache 2.4 geïnstalleerd. Het is echt geen simpele klus om die versie te gebruiken in combinatie met de package manager Homebrew. Dus de oplossing is om Apache 2.4 te installeren via Homebrew en het dan te configureren.  
Als Apache reeds zou lopen op de achtergrond, moeten we die eerst stoppen en afsluiten.

{% highlight bash %} 
$ sudo apachectl stop
$ sudo launchctl unload -w /System/Library/LaunchDaemons/org.apache.httpd.plist 2>/dev/null
$ brew install httpd24 --with-privileged-ports --with-http2
{% endhighlight %}

Dit kan even duren, maar eens de installatie voltooid is, zal je een melding krijgen:
{% highlight bash %} 
/usr/local/Cellar/httpd24/2.4.27: 212 files, 4.4M, built in 1 minute 45 seconds
{% endhighlight %}

Bewaar dat pad en vooral de versie, want dat hebben we hieronder nodig. `/usr/local/Cellar/httpd24/2.4.27`  
Als je een nieuwere versie hebt, gebruik dan die versie.

{% highlight bash %} 
$ sudo cp -v /usr/local/Cellar/httpd24/2.4.27/homebrew.mxcl.httpd24.plist /Library/LaunchDaemons
$ sudo chown -v root:wheel /Library/LaunchDaemons/homebrew.mxcl.httpd24.plist
$ sudo chmod -v 644 /Library/LaunchDaemons/homebrew.mxcl.httpd24.plist
$ sudo launchctl load /Library/LaunchDaemons/homebrew.mxcl.httpd24.plist
{% endhighlight %}

En voila, je hebt nu de Homebrew's Apache geïnstalleerd. Het is reeds opgestart, dus je kan het uittesten door naar je favoriete browser te gaan en daar **localhost** in te geven. Je zal een header te zien krijgen die aanduidt: "**It works!**". Hoera, alweer een stap dichter bij de ideale wereld.

### Probleempjes?

- Controleer of de server wel up en running is  
  `$ ps -aef | grep httpd`
- Probeer Apache te herstarten  
  `$ sudo apachectl -k restart`
- Commando's om Apache te starten, stoppen of (onmiddelijk) te herstarten
  {% highlight bash %} 
  $ sudo apachectl start
  $ sudo apachectl stop
  $ sudo apachectl -k restart
  {% endhighlight %}

Apache Configuratie
-------------------

Nu we een werkende web server hebben, gaan we het een en ander configureren zodat het beter werkt als lokale ontwikkelomgeving.

Apache zal nu naar een standaard locatie kijken waar de bestanden van zullen geladen worden. Dit heet de Document Root. Standaard is die root te vinden op `/Library/WebServer/Documents`. Wij gaan de configuratie daarvan wijzigen, dat Apache zal zoeken in de "Sites" map van de homefolder van de mac.

Maak eerst via de Finder een nieuwe map 'Sites' aan in je homefolder (in mijn geval was dit **Macintosh HD > Gebruikers > fredroeg > Sites**). Let goed op, Sites moet met een kapitaal S starten.

![alt text](http://sf.rogerthat.be/1718/pad.png "Sites path")


Geef in de terminal volgend commando in, om de configuratiefile te wijzigen
{% highlight bash %} 
$ open -e /usr/local/etc/apache2/2.4/httpd.conf
{% endhighlight %}

Zoek naar de term DocumentRoot en dan zal je de volgende lijn zien:

**VOOR**
{% highlight bash %} 
DocumentRoot "/usr/local/var/www/htdocs"
<Directory "usr/local/var/www/htdocs">
{% endhighlight %}


Zet een hashtag voor die regels, zodat we het in commentaar zetten: `#DocumentRoot "/usr/local/var/www/htdocs"`.  
Plaats dan onderstaande gegevens, die de becommentarieerde instellingen vervangen.  
**Verander fredroeg naar jouw eigen gebruikersnaam!**

**NA**
{% highlight bash %} 
#DocumentRoot "/usr/local/var/www/htdocs"
#<Directory "usr/local/var/www/htdocs">
DocumentRoot /Users/fredroeg/Sites
<Directory /Users/fredroeg/Sites>
{% endhighlight %}

Zoek in die file ook naar `<Directory>`, binnen die tag vind je een `AllowOverride` instelling terug. Die moet je wijzigen naar `all`.

{% highlight bash %} 
# AllowOverride controls what directives may be placed in .htaccess files.
# It can be "All", "None", or any combination of the keywords:
#   AllowOverride FileInfo AuthConfig Limit
#
AllowOverride All
{% endhighlight %}

Daarna zoeken naar **mod_rewrite.so**. Je komt op een regel die in commentaar staat, maar dat mag niet, haal die hashtag dus maar snel weg.

{% highlight bash %} 
LoadModule rewrite_module libexec/mod_rewrite.so
{% endhighlight %}

Ten slotte nog één instelling te wijzigen: de gebruikersinstelling. Dit zal standaard naar een gebruiker **daemon** verwijzen, maar dat zal voor problemen zorgen door de bovenstaande uitgevoerde wijzigingen.

Zoek naar **daemon** en verander dan die gegevens naar het onderstaande, let op, ook hier weer fredroeg wijzigen naar eigen gebruikersnaam.

{% highlight bash %} 
User fredroeg
Group staff
{% endhighlight %}


### Sites map
De "Sites" folder zou je via de stappen hierboven reeds moeten gemaakt hebben, zoniet doe dat dan even eerst. Binnen die Sites map zullen we nu een html-bestand plaatsen om te controleren of de apache server de nieuwe geconfugureerde map zal aanspreken. Maak via je favoriete editor ***Visual Studio Code*** een index.html aan met wat dummydata in en bewaar die html in de Sites folder.

Time to test, herstart de Apache server met volgend commando en surf dan naar http://localhost
{% highlight bash %} 
$ sudo apachectl -k restart
{% endhighlight %}

PHP Installatie
---------------

We gaan verder door PHP 5.5, PHP 5.6, PHP 7.0 en PHP 7.1 te installeren dat dmv een simpel script overschakelen van versie eenvoudig maakt.

In de terminal:
{% highlight bash %} 
$ brew install php55 --with-httpd24
$ brew unlink php55
$ brew install php56 --with-httpd24
$ brew unlink php56
$ brew install php70 --with-httpd24
$ brew unlink php70
$ brew install php71 --with-httpd24
{% endhighlight %}

Dit zal wel even duren. Als je in die volgorde alle commando's uitgevoerd hebt, zal de huidige "actieve" versie PHP 7.1 zijn.

### Apache PHP Setup - Stap 1

Je hebt nu succesvol alle php versies geïnstalleerd, maar Apache is er nog niet van op de hoogte. Je moet alweer de `/usr/local/etc/apache2/2.4/httpd.conf` wijzigen, en zoeken naar `php5_module`.

Merk op, elke PHP versie heeft nu een regel bij gecreëerd naar zeeeeer specifieke versies. Die gaan we vervangen naar meer generieke paden. Daarnaast moet er momenteel slechts 1 php versie actief zijn, zet dus de eerste 3 versies/regels in commentaar

**VOOR**
{% highlight bash %} 
LoadModule php5_module        /usr/local/Cellar/php55/5.5.38_11/libexec/apache2/libphp5.so
LoadModule php5_module        /usr/local/Cellar/php56/5.6.26_3/libexec/apache2/libphp5.so
LoadModule php7_module        /usr/local/Cellar/php70/7.0.11_5/libexec/apache2/libphp7.so
LoadModule php7_module        /usr/local/Cellar/php71/7.1.0-rc.3_8/libexec/apache2/libphp7.so
{% endhighlight %}

**NA**
{% highlight bash %} 
#LoadModule php5_module    /usr/local/opt/php55/libexec/apache2/libphp5.so
#LoadModule php5_module    /usr/local/opt/php56/libexec/apache2/libphp5.so
#LoadModule php7_module    /usr/local/opt/php70/libexec/apache2/libphp7.so
LoadModule php7_module    /usr/local/opt/php71/libexec/apache2/libphp7.so
{% endhighlight %}

Momenteel weet de Apache server nog niet 'wat te doen' met php-bestanden. Verander dat dus maar gauw door onderstaande wijzigingen te doen in het configuratiebestand `httpd.conf`.

**VOOR**
{% highlight bash %} 
<IfModule dir_module>
    DirectoryIndex index.html
</IfModule>
{% endhighlight %}

**NA**
{% highlight bash %} 
<IfModule dir_module>
    DirectoryIndex index.php index.html
</IfModule>

<FilesMatch \.php$>
    SetHandler application/x-httpd-php
</FilesMatch>
{% endhighlight %}

Vergeet niet te bewaren na de nodige wijzigingen en herstart de Apache server
{% highlight bash %} 
$ sudo apachectl -k restart
{% endhighlight %}

### Werkt het wel? Validatie...

Maak een info.php bestand aan via je favoriete editor en plaats die in de Sites folder. (de index.html mag je gerust verwijderen)  
Plak de volgende regel in die file:

{% highlight php %} 
<?php phpinfo();
{% endhighlight %}

Navigeer nu naar dat bestand door met de browser naar volgende url te gaan: `http://localhost/info.php`

![alt text](http://sf.rogerthat.be/1718/phpinfo.png "PHP Info")

### PHP switcher script

We hebben nu hardcoded in httpd aangegeven dat PHP 7.1 de versie is dat we willen gebruiken, maar er is een gemakkelijkere manier om te wisselen van PHP versie door sPHP.

{% highlight bash %} 
$ curl -L https://gist.github.com/w00fz/142b6b19750ea6979137b963df959d11/raw > /usr/local/bin/sphp
$ chmod +x /usr/local/bin/sphp
{% endhighlight %}


### PATH controleren

Dankzij de Homebrew installatie zouden onderstaande paden moeten toegevoegd zijn aan het installatieproces. Controleer even door het volgende (enkel de eerste regel, zonder dollarteken) in te geven in de terminal:
{% highlight bash %} 
$ echo $PATH
/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin
{% endhighlight %}

Als je dit niet ziet, zal je die manueel moeten toevoegen in `.profile`.

{% highlight bash %} 
$ echo 'export PATH=/usr/local/bin:/usr/local/sbin:$PATH' > ~/.profile
{% endhighlight %}

Herstart terminal zodat de wijzigingen actief zijn in een nieuwe sessie.

### Apache PHP Setup - Stap 2

Tijd om het switcher script te activeren, pas terug `/usr/local/etc/apache2/2.4/httpd.conf` aan en doorzoek de file tot je terug ***LoadModule php*** vindt.

Pas het onderstaande aan:

**VOOR**
{% highlight bash %} 
#LoadModule php5_module    /usr/local/opt/php55/libexec/apache2/libphp5.so
#LoadModule php5_module    /usr/local/opt/php56/libexec/apache2/libphp5.so
#LoadModule php7_module    /usr/local/opt/php70/libexec/apache2/libphp7.so
LoadModule php7_module    /usr/local/opt/php71/libexec/apache2/libphp7.so
{% endhighlight %}

**NA**
{% highlight bash %} 
# Brew PHP LoadModule for `sphp` switcher
LoadModule php5_module /usr/local/lib/libphp5.so
#LoadModule php7_module /usr/local/lib/libphp7.so
{% endhighlight %}

Test uit door in een nieuw terminal venster volgend commando in te geven
Controleer nadien door terug `http://localhost/info.php` te bezoeken.

{% highlight bash %} 
sphp 55
{% endhighlight %}

![alt text](http://sf.rogerthat.be/1718/sphp.png "PHP Info na sphp")

MySQL Installatie
-----------------

Dit kan terug via `brew` gebeuren. 

Installeer MariaDB
{% highlight bash %} 
$ brew install mariadb
$ mysql_install_db
{% endhighlight %}

Na een succesvolle installatie start je de server op:
{% highlight bash %} 
$ mysql.server start
{% endhighlight %}

Het is aangeraden om de MySQL server te beveiligen en er credentials voor aan te maken. Geef onderstaand script in en volg de instructies. Voor het wachtwoord mag je de term `root` gebruiken.
{% highlight bash %} 
$ /usr/local/bin/mysql_secure_installation
{% endhighlight %}

### Sequel Pro

Sequel Pro is een gratis applicatie om databases te beheren. Download en installeer het op jouw Mac.  
Start de applicatie en connecteer met de mysql server via de Socket. ![alt text](http://sf.rogerthat.be/1718/sequelpro.png "Sequel Pro Connecteer via de Socket")

Apache Virtuele Hosts
---------------------

Een handige development tool is gebruikmaken van meerdere virtuele hosts voor de vershillende projecten. Dit wil zeggen dat je namen als katjesenhonden.dev (http://katjesenhonden.dev) kan gebruiken om lokaal jouw website te bouwen. 

Allereerst dienen we een instelling te wijzigen die het mogelijk maakt om gebruik te maken van virtuele hosts. Open terug `/usr/local/etc/apache2/2.4/httpd.conf`.

Verwijder de hashtags uit onderstaande regels zodat het niet langer in commentaar staat.

{% highlight bash %} 
LoadModule vhost_alias_module libexec/mod_vhost_alias.so
{% endhighlight %}

en ook hier commentaarteken (hashtag) weghalen

{% highlight bash %} 
# Virtual hosts
Include /usr/local/etc/apache2/2.4/extra/httpd-vhosts.conf
{% endhighlight %}

Nu kan je de virtuele hosts aanmaken en wijzigen. Open het bestand `httpd-vhosts.conf` en plak het volgende erin. Aandacht! **fredroeg** wijzigen naar eigen gebruikersnaam!

{% highlight bash %} 
<VirtualHost *:80>
    DocumentRoot "/Users/fredroeg/Sites"
    ServerName localhost
</VirtualHost>

<VirtualHost *:80>
    DocumentRoot "/Users/fredroeg/Sites/katjesenhonden"
    ServerName katjesenhonden.dev
</VirtualHost>
{% endhighlight %}



### .dev adressen laten werken


Om ervoor te zorgen dat `.dev` adressen werken op de localhost is er nog één uitbreiding nodig. Met behulp van ***DNSMasq*** zullen we alle domeinen die eindigen op extensie `.dev` forwarden naar de localhost.

Voer volgende commando's achtereenvolgend uit via de terminal
{% highlight bash %} 
$ brew install dnsmasq
$ echo 'address=/.dev/127.0.0.1' > /usr/local/etc/dnsmasq.conf
$ sudo brew services start dnsmasq
$ sudo mkdir -v /etc/resolver
$ sudo bash -c 'echo "nameserver 127.0.0.1" > /etc/resolver/dev'
{% endhighlight %}

Test even uit door in de terminal te **pingen** naar een `.dev` adres:  

`ping foo.dev`
{% highlight bash %} 
64 bytes from 127.0.0.1: icmp_seq=0 ttl=64 time=0.044 ms
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.118 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.045 ms
...
{% endhighlight %}



Als er nu naar `http:/katjesenhonden.dev` gesurft wordt via je mac, zal de brondirectory van die lokale site de folder katjesenhonden zijn in de map **Sites**. (TIP: test even uit met een index.php bestand)


> Source: [macOS 10.12 Sierra Apache Setup: MySQL, APC & More...](https://getgrav.org/blog/macos-sierra-apache-mysql-vhost-apc) 2016, updated & translated for Artevelde University College 
{:.card.card-definition}
