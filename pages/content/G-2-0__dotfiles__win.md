---
layout   : course
permalink: dotfiles/win/
published: true
#
abbreviations:
  - kbd
hyperlinks:
  - software
title     : Windows
title_long: Dotfiles Installeren op Windows
---
{%- include includes.md %}

> Opmerking
> ---
> Deze installatie-instructies zijn bedoeld voor *&nbsp;*{:.fab.fa-fw.fa-windows}**Windows 10** 1803 (Versie 10.0.**17134.285**), maar werken waarschijnlijk ook voor andere versies van Windows.
{:.card.card-remark}

> Tip
> ---
> Installeer de **allerlaatste versie** van Windows.
>
><kbd class="menu"><kbd><i class="fab fa-windows"></i></kbd>&#9656;<kbd>Instellingen</kbd>&#9656;<kbd>Bijwerken en Beveiliging</kbd>&#9656;<kbd>Naar updates zoeken</kbd></kbd>
>
> Als de allerlaatste update (nog) niet beschikbaar is, kan die installeren met [Windows 10 Upgrade](https://www.microsoft.com/nl-nl/software-download//windows10).
{:.card.card-tip}

Benodigdheden
-------------

### Teksteditor

[*&nbsp;*{:.fas.fa-fw.fa-download}Visual Studio Code voor Windows](https://code.visualstudio.com/download){:.button.button--standard.button--primary}

Om te testen of de opdracht goed geïnstalleerd is, open je de **Opdrachtprompt** *(Command)* en vraag je de versie (`--version`) van Visual Studio Code (`code`) op. 

{% highlight cmd %}
C:> code --version
{% endhighlight %}

Nu kan je vanuit de **Opdrachtprompt** *(Command)* bestanden open met [Visual Studio Code][].

### Scoop

Open **Windows Powershell** en voer onderstaande opdracht uit.

{% highlight posh %}
PS> iex (new-object net.webclient).downloadstring('https://get.scoop.sh')
{% endhighlight %}

### Git

Open **Windows Powershell** en voer onderstaande opdracht uit.

{% highlight posh %}
PS> scoop install git
{% endhighlight %}

### PowerShell Core
{%- assign PowerShell-version = '6.1.0' %}

Download de *installer* (`.msi`) onderaan de pagina voor PowerShell Core {{ PowerShell-version }} of later:

[*&nbsp;*{:.fas.fa-fw.fa-download}PowerShell Core voor Windows][PowerShell]{:.button.button--standard.button--primary}

Na de installatie open je **PowerShell Core {{ PowerShell-version }}** als **administrator**.

> Opmerking
> ---
> **PowerShell Core {{ PowerShell-version }}** is niet hetzelfde als **Windows PowerShell** of **Windows PowerShell ISE**!
{:.card.card-remark}

> Opgelet
> ---
> Open **PowerShell Core {{ PowerShell-version }}** ALTIJD als **administrator**.
{:.card.card-warning}

> Windows
> ---
> Om **PowerShell Core {{ PowerShell-version }}** altijd als administrator te openen, open je eerst de bestandslocatie.  
> <kbd class="menu"><kbd><i class="fab fa-windows"></i></kbd>&#9656;<kbd>PowerShell {{ PowerShell-version }}</kbd>&#9656;<kbd>RMK</kbd>&#9656;<kbd>Bestandslocatie openen</kbd></kbd>  
> Pas vervolgens de eigenschappen van het bestand aan.  
> <kbd class="menu"><kbd><i class="fa fa-file-o"></i> PowerShell Core {{ PowerShell-version }}</kbd>&#9656;<kbd>RMK</kbd>&#9656;<kbd>Eigenschappen</kbd>&#9656;<kbd>Geavanceerd...</kbd>&#9656;<kbd>Als administrator uitvoeren</kbd></kbd>
{:.card.card-windows}

Installatie
-----------

### Repository klonen

> Opgelet
> ---
> Zorg ervoor dat je op school via *&nbsp;*{:.fas.fa-fw.fa-wifi} Artevelde HS **Open** verbindt totdat de dotfiles geïnstalleerd zijn!
{:.card.card-warning}

Ga naar de Home-map en kloon de GitHub-repository.

{% highlight posh %}
PS> Set-Location -Path $Home
PS> git clone https://github.com/gdmgent/dotfiles.git --single-branch
{% endhighlight %}

### Profiel instellen

Ga naar de gekloonde Dotfiles-map en voer het installatiescript uit.

{% highlight posh %}
PS> Set-Location -Path dotfiles
PS> Unblock-File .\install.ps1
PS> Unblock-File .\modules\*.psm1
PS> Set-ExecutionPolicy -ExecutionPolicy Unrestricted
PS> .\install.ps1
{% endhighlight %}

Open een nieuw **PowerShell Core {{ PowerShell-version }}**-venster en je zou `gdm.gent Dotfiles 0000.00.00a in PowerShell Core {{ PowerShell-version }} on Windows` te zien moeten krijgen, zonder rode foutmeldingen.
