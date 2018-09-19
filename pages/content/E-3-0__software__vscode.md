---
layout   : course
permalink: software/vscode/
published: true
#
title     : Visual Studio Code
title_long: Microsoft Visual Studio Code
---

Inleiding
---------

> Microsoft Visual Studio Code
> ----------------------------
> Is klein en licht, maar bevat een sterke source code editor die draait op je desktop en is beschikbaar voor Windows, Mac en Linux. Het bevat ondersteuning voor JavaScript, TypeScript en Node.js en heeft een rijk ecosystem van extensies voor andere talen, zoals C++, C#, Python, PHP, Go …
{:.card.card-definition}

Voorlopig worden reeds meer dan 30 programmeertalen ondersteund, zoals: JavaScript, C#, C++, PHP, Java, HTML, CSS, SQL, … . Het editeren is gefocused op het schrijven van code (multiple cursors, autosave, …). Deze editor bevat verschillende features:

- snel zoeken via RegEx;
- definities van klassen e.d. bekijken;
- code outline;
- intellisense;
- debugging;
- git version control;
- vorm aanpasbaar door de gebruiker;
- uitbreidbaar via extensions;
- ... .

Installatie via Executables
---------------------------

Op 12-09-2017 bedraagt de laatste versienummer **1.16**.

### Op Windows

Download de **64-bit** versie om Microsoft Visual Studio Code ten volle te gebruiken!

Download via: <https://code.visualstudio.com/docs/?dv=win>

### Op macOS

1. Download via: <https://code.visualstudio.com/docs/?dv=osx>;
1. Dubbel-klik op het gedownloade arhiveerbestand om te inhoud uit te pakken;
1. Sleep de `Visual Studio Code.app` naar de Applicatiefolder (Applications folder), zodat deze beschikbaar is in het Launchpad.
1. Voeg VS Code toe aan de Dock door rechts te klinnen op het icoon en vervolgens te kiezen voor **Options, Keep in Dock**.

Command Line
------------

We kunnen VS Code ook uitvoeren via de terminal door het commando `code` te typen, nadat we dit commando toegevoegd hebben aan de `$PATH` waarde uit het systeem. Om dit te verwezenlijken lanceren we VS Code, vervolgens openen we het **Command Palette** via ⇧⌘P (macOS) of Cntrl+P (Windows) en typen hier `> shell command` om het commando `Shell Command: Install 'code'`. Herstart de terminal zodat de nieuwe waarde voor `$PATH` van kracht is.

Extensies
---------

> Definitie
> ---
> Een **extensie** is een uitbreiding van een toepassing die extra functionaliteit toevoegt.
{:.card.card-definition}

> Zie ook
> ---
> Extension Marketplace  
> - <https://code.visualstudio.com/docs/editor/extension-gallery>
> - <https://marketplace.visualstudio.com/vscode>
{:.card.card-link}

> Visual Studio Code
> ---
> Installeer een extensie de **Extensions** te openen met:  
> <kbd class="keyboard"><kbd>&#8679; Shift</kbd>+<kbd>Cmd</kbd>+<kbd>X</kbd></kbd> of
> <kbd class="keyboard"><kbd>&#8679; Shift</kbd>+<kbd>Ctrl</kbd>+<kbd>X</kbd></kbd>
{:.card.card-app}

- [Debugger for Chrome](https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome)  
  `ext install debugger-for-chrome`
- [beautify](https://marketplace.visualstudio.com/items?itemName=HookyQR.beautify)  
  `ext install beautify`
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)  
`ext install vscode-eslint`
- [jshint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.jshint)  
  `ext install jshint` 
- [HTML CSS Support](https://marketplace.visualstudio.com/items?itemName=ecmel.vscode-html-css)  
  `ext install vscode-html-css` 
- [Auto Close Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-close-tag)  
  `ext install auto-close-tag` 
- [Auto Rename Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag)  
  `ext install auto-rename-tag`
- [Sass](https://marketplace.visualstudio.com/items?itemName=robinbentley.sass-indented)  
  `ext install sass-indented` 
- [One Dark Pro](https://marketplace.visualstudio.com/items?itemName=zhuangtongfa.Material-theme)  
  `ext install Material-theme` 
- [vscode-icons](https://marketplace.visualstudio.com/items?itemName=robertohuertasm.vscode-icons)  
  `ext install vscode-icons`