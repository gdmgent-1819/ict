---
layout   : course
permalink: tools/git/mac/
published: true
#
title     : macOS
title_long: Installatie git op macOS
---

Installatie via Executables
---------------------------

Open **Terminal** en voer `git --version` uit om te testen of git geïnstalleerd is.

{% highlight terminal %}
git --version
{% endhighlight %}

> Opmerking
> ---
> Indien Git nog niet geïnstalleerd is, zal een popupvenster verschijnen.
> Klik op de knop "**Installeer**" om de **Command Line Developer Tools** te installeren.
{:.card.card-definition}

Indien het popupvenster niet verschijnt, kan je het manueel starten met:

{% highlight terminal %}
xcode-select --install
{% endhighlight %}

Installatie via Package Managers
---------------------------------

Git kan op macOS ook geïnstalleerd worden via Homebrew:

{% highlight terminal %}
brew install git
{% endhighlight %}

Het is aan te raden om bij de installatie van git via Homebrew de commando's `brew update` en `brew upgrade` uit te voeren.