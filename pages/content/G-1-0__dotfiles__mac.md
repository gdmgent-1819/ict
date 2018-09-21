---
layout   : course
permalink: dotfiles/mac/
published: true
#
abbreviations:
  - cli
  - computer
  - education
  - kbd
hyperlinks:
  - software
title     : macOS
title_long: Dotfiles Installeren op macOS
---
{%- include includes.md %}

> Opmerking
> ---
> Deze installatie-instructies zijn bedoeld voor *&nbsp;*{:.fab.fa-fw.fa-apple}**macOS High Sierra** (Versie 10.**13**), maar werken waarschijnlijk ook voor andere versies van macOS.
{:.card.card-remark}

> Tip
> ---
> Installeer de **allerlaatste** versie van macOS.
>
> Enkel *minor updates* kan je via Updates installeren, voor de *major updates* moet je via de App Store de nieuwste versie downloaden.
{:.card.card-tip}

Benodigdheden
-------------

### Teksteditor

[*&nbsp;*{:.fas.fa-fw.fa-download}Visual Studio Code voor macOS](https://code.visualstudio.com/download){:.button.button--standard.button--primary}

Om [Visual Studio Code][] vanuit de macOS **Terminal** te kunnen openen met de opdracht `code`, moeten we in de applicatie eenmalig een script uitvoeren.

> Visual Studio Code
> ---
> Start de applicatie en open de **Command Palette** met <kbd class="menu"><kbd>View</kbd>&#9656;<kbd>Command Palette...</kbd></kbd> of <kbd class="keyboard"><kbd>&#8679; Shift</kbd>+<kbd>Cmd</kbd>+<kbd>P</kbd></kbd>  
> en voer `Shell Command: Install 'code' command in PATH` uit.
{:.card.card-app}

Om te testen of de opdracht goed geïnstalleerd is, open je de **Terminal** en vraag je de versie (`--version`) van Visual Studio Code (`code`) op.

> Opgelet
> ---
> Onderstaande PowerShell Core-opdracht knip je met <kbd class="keyboard"><kbd>Cmd</kbd>+<kbd>C</kbd></kbd> en plak je met <kbd>RMK</kbd> <mark class="marker--underline marker--yellow">zonder <code>$ </code> </mark> in het Terminal-venster.
{:.card.card-warning}

{% highlight terminal %}
$ code --version
{% endhighlight %}

Nu kan je vanuit de **Terminal** bestanden open met [Visual Studio Code][].

### PowerShell Core

Download de *installer* (`.pkg`) onderaan de pagina:

[*&nbsp;*{:.fas.fa-fw.fa-download}PowerShell Core voor macOS][PowerShell]{:.button.button--standard.button--primary}

Na de installatie moeten we PowerShell Core nog instellen als de standaard Shell.

<kbd class="menu"><kbd>Terminal</kbd>&#9656;<kbd>Voorkeuren&hellip;</kbd>&#9656;<kbd>Algemeen</kbd></kbd> en verander:

 - Open shells met:
   - Commando (volledig pad): `/usr/local/bin/pwsh -NoLogo`

Open een nieuw **Terminal**-venster en vraag de versie van PowerShell Core op.

> Opgelet
> ---
> Onderstaande PowerShell Core-opdracht knip je met <kbd class="keyboard"><kbd>Ctrl</kbd>+<kbd>C</kbd></kbd> en plak je met <kbd class="keyboard"><kbd>Cmd</kbd>+<kbd>V</kbd></kbd> <mark class="marker--underline marker--yellow">zonder <code>PS&gt; </code> </mark> in het PowerShell Core-venster.
{:.card.card-warning}

{% highlight posh %}
PS> $PSVersionTable.GitCommitId
{% endhighlight %}

### Command Line Developer Tools

Open **Terminal** en voer `git --version` uit om te testen of Git geïnstalleerd is.

{% highlight posh %}
PS> git --version
{% endhighlight %}

> Opmerking
> ---
> Indien [Git][] nog niet geïnstalleerd is, zal een popupvenster verschijnen.  
> Klik op de knop **Installeer** om de **Command Line Developer Tools** te installeren.
{:.card.card-remark}

Indien het popupvenster niet verschijnt, kan je het manueel starten met:

{% highlight posh %}
PS> xcode-select --install
{% endhighlight %}

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
PS> git clone https://github.com/gdmgent/dotfiles/ --single-branch
{% endhighlight %}


### Profiel instellen

Ga naar de gekloonde Dotfiles-map en voer het installatiescript uit.

{% highlight posh %}
PS> Set-Location -Path dotfiles
PS> .\install.ps1
{% endhighlight %}

Open een nieuw **Terminal**-venster en je zou `gdm.gent Dotfiles on PowerShell Core for macOS` te zien moeten krijgen, zonder rode foutmeldingen.


Post-installatie
----------------

### Homebrew & Homebrew Cask

#### Homebrew

##### Homebrew is nog niet geïnstalleerd

[Homebrew][] is een *package manager* voor macOS. Packages worden **formulae** voor **brews** genoemd, en opgeslagen in een **cellar**.

Open **Terminal** en installeer Homebrew door het [Dotfiles][]-script uit te voeren.

{% highlight posh %}
PS> InstallBrew
{% endhighlight %}

{% highlight posh %}
PS> brew --version
{% endhighlight %}

Je kan eventuele problemen detecteren met de Homebrew-opdracht `doctor`. Volg indien nodig het advies.

{% highlight posh %}
PS> brew doctor
{% endhighlight %}

##### Homebrew is al geïnstalleerd

Als Homebrew al eerder geïnstalleerd werd, moet je deze stappen doorlopen:

| Stap | Opdracht       | Verklaring                                       |
|:----:|----------------|--------------------------------------------------|
|   1  | `brew update`  | Update naar de nieuwste versie van Homebrew.     |
|   2  | `brew upgrade` | Waardeer alle verouderde formulae op.            |
|   3  | `brew cleanup` | (Optioneel: verwijder alle verouderde formulae.) |
{:.table}

Door het [Dotfiles][]-script uit te voeren kan je de drie stappen in een keer uitvoeren.

{% highlight posh %}
PS> UpdateBrew
{% endhighlight %}

> Tip
> ---
> Verouderde formulae kunnen verwijderd worden met de Homebrew-opdracht `cleanup`. Soms is het echter beter om de oudere versies te bewaren zodat je die opnieuw kan installeren mochten er problemen zijn met nieuwe versies. Gebruik `brew switch` om vorige versies opnieuw te installeren.
{:.card.card-tip}

#### Homebrew Cask

[Homebrew Cask][Cask] is een **Homebrew**-uitbreiding om **Casks** (macOS-applicaties met een grafische interface) te installeren vanaf de Terminal.

{% highlight posh %}
PS> brew tap caskroom/cask
{% endhighlight %}

#### Git

Op macOS wordt [Git][] samen met de *Xcode Command Line Tools* geïnstalleerd. Het kan echter handig zijn om de allerlaatste versie te hebben. Deze versie kan je met Homebrew installeren.

{% highlight posh %}
PS> InstallGit
{% endhighlight %}

> Tip
> ---
> Je kan nagaan wat het pad is naar het uitvoerbaar bestand dat standaard aangeroepen wordt, door de opdracht `which` te gebruiken.
{:.card.card-tip}

{% highlight posh %}
PS> which git
{% endhighlight %}