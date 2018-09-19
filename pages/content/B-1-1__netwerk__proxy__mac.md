---
layout   : course
permalink: netwerk/proxy/mac/
published: false
#
title     : macOS
title_long: Proxyserverinstellingen voor macOS
---

> Opgelet
> ---
> Deze proxyinstellingen zijn enkel geldig voor de **Terminal** en zijn onafhankelijk van de systeeminstellingen.
{:.card.card-warning}

Handmatig
---------

Je kan de proxyserverinstellingen handmatig invoeren.

### Instellen

De proxyserverinstellingen invoeren voor de rest van de sessie.

{% highlight terminal %}
$ PXY=http://proxy.arteveldehs.be:8080 && NOPXY=localhost,127.0.0.1,.local && export HTTP_PROXY=$PXY HTTPS_PROXY=$PXY FTP_PROXY=$PXY NO_PROXY=$NOPXY http_proxy=$PXY https_proxy=$PXY ftp_proxy=$PXY no_proxy=$NOPXY && unset PXY NOPXY
{% endhighlight %}

### Ongedaan maken

De proxyserverinstellingen ongedaan maken met de opdracht `unset`, of sluit gewoon het Terminal-venster en open een nieuw.

{% highlight terminal %}
$ unset HTTP_PROXY HTTPS_PROXY FTP_PROXY NO_PROXY http_proxy https_proxy ftp_proxy no_proxy
{% endhighlight %}

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