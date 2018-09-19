---
layout   : course
permalink: netwerk/proxy/win/
published: false
#
title     : Windows
title_long: Proxyserverinstellingen voor Windows
---

Handmatig
---------

Je kan de proxyserverinstellingen handmatig invoeren.s

> Windows
> ---
> Open de gebruikersvariabelen.  
> <kbd class="menu"><kbd>Omgevingsvariabelen…</kbd>&#9656;<kbd>Gebruikersvariabelen</kbd></kbd>
{:.card.card-windows}

| Variable      | Waarde                             |
|:--------------|:-----------------------------------|
| `HTTP_PROXY`  | `http://proxy.arteveldehs.be:8080` |
| `HTTPS_PROXY` | `http://proxy.arteveldehs.be:8080` |
| `FTP_PROXY`   | `http://proxy.arteveldehs.be:8080` |
| `NO_PROXY`    | `localhost,127.0.0.1,.local`       |
{:.table}

> Tip
> ---
> Om de proxyserverinstellingen tijdelijk uit te schakelen kan je de naam van de variabelen wijzigen.
> Zet er bijvoorbeeld een `!` voor.
{:.card.card-tip}

Via een script
--------------

### Instellen

Schakel de proxyserverinstellingen uit met de switch `on`.

{% highlight posh %}
PS> proxy on
{% endhighlight %}

### Ongedaan maken

Schakel de proxyserverinstellingen uit met de switch `off`.

{% highlight posh %}
PS> proxy off
{% endhighlight %}