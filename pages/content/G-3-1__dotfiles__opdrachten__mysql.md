---
layout   : course
permalink: dotfiles/opdrachten/mysql/
published: true
#
abbreviations:
  - cli
  - education
hyperlinks:
  - education
  - software
  - technology
title     : MySQL
title_long: MySQL Installeren
---
{%- include includes.md %}

Afspraken
---------

| Gebruiker       | Wachtwoord      | Database       | Rol in de db | OLOD                                      |
|-----------------|-----------------|----------------|--------------|-------------------------------------------|
| `root`          | `secret`        | *Alle*         | Beheerder    | *Alle*                                    |
|-----------------|-----------------|----------------|--------------|-------------------------------------------|
| `cms-user`      | `cms-pass`      | `cms-db`       | Gebruiker    | [CMS][Syllabus CMS 2017-18]               |
| `cmsdev-user`   | `cmsdev-pass`   | `cmsdev-db`    | Gebruiker    | [CMSDEV][Syllabus CMSDEV 2017-18]         |
| `webdev1-user`  | `webdev1-pass`  | `webdev1-db`   | Gebruiker    | [WEBDEV-I][Syllabus WEBDEV-I 2017-18]     |
| `webdev2-user`  | `webdev2-pass`  | `webdev2-db`   | Gebruiker    | [WEBDEV-II][Syllabus WEBDEV-II 2017-18]   |
| `webtech2-user` | `webtech2-pass` | `webtech2-db`  | Gebruiker    | [WEBTECH-II][Syllabus WEBTECH-II 2017-18] |
{:.table.table--primary}

Installatie
-----------

### macOS

Open PowerShell en start het installatiescript om [MySQL][] via [Homebrew][] te downloaden en te installeren.

{% highlight posh %}
PS> InstallMySQL
{% endhighlight %}

### Windows

Open PowerShell en start het installatiescript om de [MySQL Installer][] te downloaden en te starten.

{% highlight posh %}
PS> InstallMySQL
{% endhighlight %}

{% include shared/figure.html src="content/mysql-installer_01.png" alt="MySQL Installer 01" number="01" caption="<strong>MySQL Installer</strong> Adding Community<br>Choosing a Setup Type &#9656; Custom<br><kbd>Next ></kbd>" local=true %}
{% include shared/figure.html src="content/mysql-installer_02.png" alt="MySQL Installer 02" number="02" caption="<strong>MySQL Installer</strong> Adding Community<br>Select Products and Features &#9656; <em>MySQL Server 5.7</em> - <strong>X64</strong><br>en optioneel ook <em>MySQL Workbench</em> - <strong>X64</strong><br><kbd>Next ></kbd>" local=true %}
{% include shared/figure.html src="content/mysql-installer_03.png" alt="MySQL Installer 03" number="03" caption="<strong>MySQL Installer</strong> Adding Community<br>Installation<br><kbd>Execute</kbd>" local=true %}
{% include shared/figure.html src="content/mysql-installer_04.png" alt="MySQL Installer 04" number="04" caption="<strong>MySQL Installer</strong> Adding Community<br>Installation<br><kbd>Next ></kbd>" local=true %}
{% include shared/figure.html src="content/mysql-installer_05.png" alt="MySQL Installer 05" number="05" caption="<strong>MySQL Installer</strong> Adding Community<br>Product Configuration<br><kbd>Next ></kbd>" local=true %}
{% include shared/figure.html src="content/mysql-installer_06.png" alt="MySQL Installer 06" number="06" caption="<strong>MySQL Installer</strong> MySQL Server<br>Type and Networking &#9656; Standalone MySQL Server / Classic MySQL Replication<br><kbd>Next ></kbd>" local=true %}
{% include shared/figure.html src="content/mysql-installer_07.png" alt="MySQL Installer 07" number="07" caption="<strong>MySQL Installer</strong> MySQL Server<br>Type and Networking<br><kbd>Next ></kbd>" local=true %}
{% include shared/figure.html src="content/mysql-installer_08.png" alt="MySQL Installer 08" number="08" caption="<strong>MySQL Installer</strong> MySQL Server<br>Accounts and Roles &#9656; MySQL Root Password: <code>secret</code><br><kbd>Next ></kbd>" local=true %}
{% include shared/figure.html src="content/mysql-installer_09.png" alt="MySQL Installer 09" number="09" caption="<strong>MySQL Installer</strong> MySQL Server<br>Windows Service<br><kbd>Next ></kbd>" local=true %}
{% include shared/figure.html src="content/mysql-installer_10.png" alt="MySQL Installer 10" number="10" caption="<strong>MySQL Installer</strong> MySQL Server<br>Plugins and Extensions<br><kbd>Next ></kbd>" local=true %}
{% include shared/figure.html src="content/mysql-installer_11.png" alt="MySQL Installer 11" number="11" caption="<strong>MySQL Installer</strong> MySQL Server<br>Apply Configuration<br><kbd>Execute</kbd>" local=true %}
{% include shared/figure.html src="content/mysql-installer_12.png" alt="MySQL Installer 12" number="12" caption="<strong>MySQL Installer</strong> MySQL Server<br>Apply Configuration<br><kbd>Finish</kbd>" local=true %}
{% include shared/figure.html src="content/mysql-installer_13.png" alt="MySQL Installer 13" number="13" caption="<strong>MySQL Installer</strong> Adding Community<br>Product Configuration<br><kbd>Next ></kbd>" local=true %}
{% include shared/figure.html src="content/mysql-installer_14.png" alt="MySQL Installer 14" number="14" caption="<strong>MySQL Installer</strong> Adding Community<br>Installation Complete<kbd>Finish</kbd>" local=true %}
{% include shared/figure.html src="content/mysql-installer_15.png" alt="MySQL Installer 15" number="15" caption="<strong>MySQL Installer</strong><br>Gebruik <em>Upgrade &hellip;</em> om de geïnstalleerde software nadien bij te werken" local=true %}

Post-installatie
----------------

Inloggen op de database als `root` voor de het OLOD [CMS][Syllabus CMS 2017-18].

{% highlight posh %}
PS> MySQLLogin -Course cms -Root
{% endhighlight %}
