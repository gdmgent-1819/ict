---
layout   : course
permalink: dotfiles/opdrachten/php/
published: true
#
abbreviations:
  - cli
hyperlinks:
  - csse
  - software
title     : PHP
title_long: PHP Installeren
---
{%- include includes.md %}

Installatie
-----------

### PHP Installeren

{% highlight posh %}
PS> InstallPhp
{% endhighlight %}

Composer Installeren
--------------------

{% highlight posh %}
PS> InstallComposer
{% endhighlight %}

### CGR (Composer Global Require)

{% highlight posh %}
PS> InstallComposerCgr
{% endhighlight %}

### Global Require

Installeer [`psy/psysh`](https://packagist.org/packages/psy/psysh) globaal.

{% highlight posh %}
PS> ComposerGlobalRequire psy/psysh
{% endhighlight %}

Andere interessante packages:
{%- assign packagist = 'https://packagist.org/packages/' %}

 - [`friendsofphp/php-cs-fixer`]({{ packagist | append: 'friendsofphp/php-cs-fixer' }})
 - [`laravel/installer`]({{ packagist | append: 'laravel/installer' }})
 - [`laravel/lumen-installer`]({{ packagist | append: 'laravel/lumen-installer' }})
 - [`symfony/symfony-installer`]({{ packagist | append: 'symfony/symfony-installer' }})
 - [`wp-cli/wp-cli`]({{ packagist | append: 'wp-cli/wp-cli' }})

### Composer en Packages Updaten

#### Globaal Updaten

{% highlight posh %}
PS> UpdateComposer
{% endhighlight %}

#### Lokaal Updaten

{% highlight posh %}
PS> UpdateComposer -Local
{% endhighlight %}
