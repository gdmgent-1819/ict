---
layout   : course
permalink: dotfiles/opdrachten/ruby/
published: true
#
hyperlinks:
  - csse
  - software
title     : Ruby
title_long: Ruby Installeren
---
{%- include includes.md %}

Installatie
-----------

Installeer eerst [Ruby][] met `InstallRuby`

{% highlight posh %}
PS> InstallRuby
{% endhighlight %}

Open het PowerShell Core-venster opnieuw.

Op Windows moet je ook nog de DeveloperKit installeren.

{% highlight posh %}
PS> InstallRubyDevelopmentKit
{% endhighlight %}

Bundler Installeren
-------------------

Installeer de Ruby Bundler Gem met `InstallBundler`

{% highlight posh %}
PS> InstallBundler
{% endhighlight %}

Jekyll Installeren
------------------

Maak eerst een map waarin het Jekyll-project moet komen.

{% highlight posh %}
PS> c
PS> New-Item -Name mijn-jekyll-project -ItemType Directory
{% endhighlight %}

Daarna kan je in de map een `Gemfile` maken om [Jekyll][] met Bundler te installeren of te updaten. Dit doe je met `UpdateBundler`.

{% highlight posh %}
PS> Set-Location mijn-jekyll-project
PS> New-Item -Name Gemfile -ItemType File
{% endhighlight %}

Open de map met Visual Studio Code

{% highlight posh %}
PS> code .
{% endhighlight %}

{% highlight ruby linenos %}
source 'http://rubygems.org'
gem 'github-pages'
gem 'wdm', '>= 0.1.1' if Gem.win_platform?
{% endhighlight %}{:data-file="Gemfile" }

{% highlight posh %}
PS> UpdateBundler
{% endhighlight %}