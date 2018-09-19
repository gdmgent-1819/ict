---
layout   : course
permalink: software/mamp/
published: true
#
title     : MAMP
title_long: My Apache - MySQL - PHP
---

Inleiding
---------

> MAMP
> ----
> Installeert een lokale server omgeving (environment) op jouw computer. Het wordt voornamelijk gebruikt om dynamische websites te maken. De installatie van MAMP heeft geen invloed op andere geïnstalleerde server omgevingen.
{:.card.card-definition}

Installatie
-----------

Download via: <https://www.mamp.info/en/> en installeer.

Configuratie
------------

### Foutmeldingen

Standaard staan foutmeldingen niet aan bij MAMP. Dit is uiteraard niet handig als je aan het ontwikkelen bent. We kunnen dit via het `php.ini` bestand aanpassen.

Ga via verkenner/finder naar de plaats waar je MAMP hebt geinstalleerd. Meestal is dit bij:
- Windows: `C:\Mamp\`
- macOS: `Applications/Mamp/`

1. Daarna ga je naar `bin/php/x.y/conf/` en open het bestand `php.ini` in VS Code.
1. Ga op zoek naar de regel waarop staat `display_errors=Off` en pas deze aan naar `display_errors=On`. Daarnaast moet ook volgende regel aanwezig zijn: `Error_reporting = E_ALL`.
1. Bestand opslaan en start de MAMP servers opnieuw.
1. Maak nu een `test.php` bestand aan in de `htdocs` folder van MAMP en schrijf daarin volgende code:

{% highlight php linenos %}
<?php

print("The line below will generate an error.<br>");
printaline("This is the line that will generate an error.");
print("This line will not be displayed due to the error caused by the above line.");
{% endhighlight %}{:data-file="test.php"}
