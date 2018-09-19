---
layout   : course
permalink: tools/github/
published: true
#
title: GitHub
---

Inleiding
---------

> Definitie
> ---
> **GitHub** is een webgebaseerde (web-based) service om software development projecten te herbergen (hosten) gebruik makend van het Git revisie (revision control) beheersysteem. Het wordt veel gebruikt voor open-source software development projecten. 
{:.card.card-definition}

GitHub bevat de volgende plannen:

- Private repositories (betalend);
- Public repositories (gratis en open-source);
- GitHub Enterprise (GitHub systeem opzetten op eigen servers).

Via GitHub (of BitBucket, GitLab, ...) kunnen meerdere mensen samenwerken aan 1 of meerdere repositories d.m.v. een remote server. Elk teamlid van een repository heeft meestal een lokale kopie van deze repository staan, en kan zijn / haar lokale wijzigingen doorvoeren naar de remote server. De andere teamleden kunnen dan hun lokale kopie synchroniseren met de remote server.

Aanmaak GitHub account
----------------------

We zullen voor het academiejaar 2018-19 éénmalig een [GitHub-account](https://github.com/join?source=header-home) aanmaken, deze bevat de volgende samenstelling: `gdm-1819-{your AHS-loginname}`, bv.: `gdm-1819-phildp` (allemaal lowercase pf kleine letters). Gebruik ook jouw AHS-emailadres en jouw echte naam. Vergeet ook niet een duidelijke foto te plaatsen bij jouw profiel. GitHub zorgt voor jullie en biedt ook gratis een [packs for education](https://education.github.com/pack/join) aan. Dit is o.a. handig om **private repositories** aan te maken.

Heb je al een account op GitHub die jouw AHS-emailadres gebruikt, dan volstaat het enkel jouw gebruikersnaam te veranderen via [Account](https://github.com/settings/admin). Deze wijziging duurt een paar minuten en kan ervoor zorgen dat o.a. links naar persoonlijke Gists niet meer zullen werken.

Open vervolgens de terminal (macOS) of command prompt (Windows) waarin we onze GitHub-loginnaam en GitHub e-mailadres zullen linken aan onze computer:

{% highlight bash %}
git config --global user.name "gdm-1718-{your GitHub-username}"
git config --global user.email "{your GitHub-email address}"
{% endhighlight %}

Bijvoorbeeld:

{% highlight bash %}
git config --global user.name "gdm-1718-phildp"
git config --global user.email "philippe.depauw@arteveldehs.be"
{% endhighlight %}