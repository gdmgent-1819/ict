---
layout   : course
permalink: tools/git/
published: true
#
title: Git
title_long: Git
---

Inleiding
---------

> Git
> ---
> **Git** staat voor **"Global Information Tracker"**. Het is een revisie (revision control) beheersysteem en een broncode (source code) management systeem (SCM) vergelijkbaar met het alomgekende **SVN**-systeem (2001 e.v.). 
{:.card.card-definition}

Het Git-systeem, initieel ontwikkeld door Linus Torvalds voor de Linux Kernel Development in 2005, voldoet aan een aantal vereisten (requirements):

- gratis;
- eenvoudig, snel en efficiënt;
- betrouwbaar;
- schaalbaar (scalable)  
  Met honderden teamleden kunnen samenwerken aan hetzelfde project.
- geschiedenis  
  Weten wie wat gedaan heeft en wanneer?
- transacties;
  Meerdere acties bundelen.
- ondersteuning voor branches  
  Afsplitsing van het hoofdproject die later terug kan samengevoegd worden met het hoofdproject.
- ...

Iedere Git-werkmap bevat een volledige **repository** met een overzicht van de geschiedenis en bevat ook **tracking capaciteiten**. Git is niet afhankelijk van een centrale opslagplaats! 

Nieuwe versies van een app worden eerst **lokaal bewaard** in een **lokale copy van de centrale opslagplaats** (server). Deze lokale opslagplaats kan later **gesynchroniseerd** worden met de centrale opslagplaats. **Conflicten** in versies worden aangeduid door de Git-software, zodat een teamlid deze kan oplossen!

Installatie 
-----------

 - [Installatie op macOS]({{ site.baseurl }}{% link pages/content/6-2-1__tools__git__mac.md %})
 - [Installatie op Windows]({{ site.baseurl }}{% link pages/content/6-2-2__tools__git__win.md %})

Configuratie
------------

### Identiteit

Het eerste dat we moeten doen nadat we Git hebben geïnstalleerd is om onze gebruikersnaam en e-mailadres in te stellen. Dit is belangrijk omdat elk **Git commit** commando deze informatie gebruikt om het commit object te ondertekenen. Deze informatie zit vervat als meta-informatie in een commit beschrijving.

{% highlight bash %}
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
{% endhighlight %}

Bijvoorbeeld:

{% highlight bash %}
git config --global user.name "drdynscript"
git config --global user.email "philippe.depauw@arteveldehs.be"
{% endhighlight %}

Dit hoeft enkel maar **eenmaal** uitgevoerd te worden omdat we de `--global` optie vermelden. Git zal steeds deze instellingen gebruiker voor alles wat je gerelateerd doet op het systeem. Indien we deze instellingen willen overschrijven voor een project, dan voeren we deze commando's uit zonder de `--global` optie.

### Forceren van `https` i.p.v. `git`

Binnen het netwerk van de Arteveldehogeschool wordt het `git-protocol` geblokkeerd door de firewall. We kunnen dit protocol vervangen door `https`via de volgende configuratie:

{% highlight bash %}
git config --global url."https://".insteadOf git://
{% endhighlight %}

Op deze manier gebruiken we altijd `https`-protocol i.p.v. `git`-protocol. De overdracht van data zal dus voortaan geschieden via `https`.

### Editor

Now that your identity is set up, you can configure the default text editor that will be used when Git needs you to type in a message. By default, Git uses your system’s default editor, which is generally Vi or Vim. If you want to use a different text editor, such as Emacs, you can do the following:

Via configuratie kunnen we de standaard editor instellen, die Git zal gebruiken wanneer we een boodschap (message) moeten typen. Standaard wordt de "default" editor van het besturingssysteem gebruikt: notepad (Windows), vi of vim (macOS), ... .

{% highlight bash %}
git config --global core.editor emacs
{% endhighlight %}

VS Code kunnen we instellen als default editor:

{% highlight bash %}
git config --global core.editor "code --wait"
{% endhighlight %}

### Merge en Diff tool

Specifiëren van de standaard "merge tool" om "merge conflicts" op te lossen.

Another useful option you may want to configure is the default diff tool to use to resolve merge conflicts. Say you want to use vimdiff:

vimdiff instellen als standaard "merge tool":

{% highlight bash %}
git config --global merge.tool vimdiff
git config --global diff.external vimdiff
{% endhighlight %}

VS Code kunnen we instellen als default "merge tool":

{% highlight bash %}
git config --global merge.tool vscodemerge
git config --global mergetool.vscodemerge.cmd 'code --wait --diff $LOCAL $REMOTE'
git config --global mergetool.vscodemerge.trustExitCode false
git config --global diff.external code
{% endhighlight %}

### Commit template

If you set this to the path of a file on your system, Git will use that file as the default message when you commit. For instance, suppose you create a template file at $HOME/.gitmessage.txt that looks like this:

Een commit template is een template dat door Git wordt gebruikt als standaardbericht voor een "commit". Deze template wordt gedefinieerd in een tekstbestand `.gitmessage.txt` meestal onder de home-directory.

Voorbeeld inhoud `.gitmessage.txt`bestand:

{% highlight txt %}
-> Subject

-> What have you done?

New Media Development | Graphical and Digitale Media | Artevelde University College Ghent
{% endhighlight %}

Instellen van deze template voor git commits:

{% highlight bash %}
git config --global commit.template $HOME/.gitmessage.txt
{% endhighlight %}

### Proxy-server

Binnen het netwerk van de Arteveldehogeschool zijn, zoals gekend, drie soorten netwerken beschikbaar. Connecteren we via **AHS-veilig** of via de **Ethernet-kabel**, dan moeten we de proxy-server instellen. Voor het netwerk **AHS-open** hoeven deze instellingen **niet** te gebeuren. Indien de globale proxy-instellingen niet zijn ingesteld, dan kunnen we deze instellen enkel voor Git. Dat doen we door de volgende commando's uit te voeren:

{% highlight bash %}
git config --global http.proxy "http://proxy.arteveldehs.be:8080"
git config --global https.proxy "http://proxy.arteveldehs.be:8080"
{% endhighlight %}

We kunnen ook globale proxy-instellingen gebruiken voor heel het OS, zie: [Proxyserver instellingen](../../netwerk/proxy).

Werken we op een andere locatie, buiten het netwerk van de Arteveldehogeschool, is de kans groot dat er geen proxy-server aanwezig is waardoor we deze instellingen moeten verwijderen uit het Git configuratiebestand.  Dat doen we door de volgende commando's uit te voeren:

{% highlight bash %}
git config --global --unset http.proxy
git config --global --unset https.proxy
{% endhighlight %}