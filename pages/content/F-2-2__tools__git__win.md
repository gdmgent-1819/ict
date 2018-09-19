---
layout   : course
permalink: tools/git/win/
published: true
#
title     : Windows
title_long: Installatie git op Windows 
---

Installatie via Executables
---------------------------

> Download
> --------
> <http://msysgit.github.io/>
{:.card.card-definition}

Vergeet niet de laatste of voorlaatste optie te selecteren tijdens de "Git Setup Installatie Wizard". Op deze manier kunnen we het git commando overal aanspreken (Het pad naar de Git executable wordt aan de systeemvariabelen toegevoegd)!

{% comment %}
Installatie via Package Managers
---------------------------------

Git kan op Windows ook geïnstalleerd worden via [Chocolatey](https://chocolatey.org/packages/git.install):

{% highlight cmd %}
choco install git.install
{% endhighlight %}

Om git the upgraden via Chocolatey:

{% highlight cmd %}
choco upgrade git.install
{% endhighlight %}

Het is aan te raden om bij de installatie van git of andere tools, Chocolatey te [upgraden](https://github.com/chocolatey/choco/wiki/CommandsUpgrade) via het commando `choco upgrade chocolatey`.


{% endcomment %}