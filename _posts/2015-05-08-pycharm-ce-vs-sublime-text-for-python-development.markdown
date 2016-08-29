---
published: true
title: PyCharm CE vs Sublime Text for Python Development
layout: post
permalink: /blog/2015/05/08/pycharm-ce-vs-sublime-text-for-python-development/
---
PyCharm and Sublime Text are both great editors, and they are both recommended quite often for Python development. While PyCharm is a full-fledged IDE, Sublime Text is a sophisticated text editor that is massively extensible via plugins. But which one is better?

Throughout the text of this post, whenever I say PyCharm, I am referring to PyCharm CE, and when I say Sublime, I am referring to Sublime Text 3(with Anaconda & GitGutter plugins installed).

## Autocomplete

Code completion is a very useful feature to have for Python development. To get code completion in Sublime for Python, there are multiple plugins you can use. There’s [SublimeCodeIntel](https://packagecontrol.io/packages/SublimeCodeIntel), [SublimeJEDI](https://packagecontrol.io/packages/Jedi%20-%20Python%20autocompletion), and [Anaconda](https://packagecontrol.io/packages/Anaconda). I personally prefer Anaconda.

### Imports

PyCharms support for import autocompletion is no doubt worlds better compared to what Sublime has to offer.

![](http://i.imgur.com/3cTpiTR.png?1)
![](http://i.imgur.com/ToD67A2.png?1)


(PyCharm)

![](http://i.imgur.com/otrssoy.png?1)
![](http://i.imgur.com/fuejKGj.png?1)


(Sublime)

For some reason, it seems Anaconda doesn’t want to offer autocompletion without the `from … import …` syntax.

### Functions

For functions, both Sublime and PyCharm have quality autocompletion. With Anaconda, it is possible to combine the docstring with the method signature, while you will have to settle with `Ctrl+J` on PyCharm.

![](http://i.imgur.com/3UIR7On.png?1)


(Sublime)

![](http://i.imgur.com/3eh4InA.png?1)


(PyCharm)

One place where PyCharm is lacking is automatic parameter insertion. While Sublime supports automatic parameter insertion, PyCharm only has automatic parameter hinting.

![](http://media.giphy.com/media/3o85xJK7YcHcb6Fz0Y/giphy.gif)


(Sublime)

![](http://media.giphy.com/media/3o85xI1eqrPPgJkZna/giphy.gif)


(PyCharm)


Score:
PyCharm - 2.5 points
Sublime - 3 points

## Virtual Environments

Both Sublime and PyCharm have support for virtualenv, while only Sublime supports Vagrant. Both Sublime and PyCharm can lint code using a virtual environment. If you are on Linux or OSX, you can symlink a virtual environment from within a Vagrant VM, but doing so is not possible on Windows.


Score:
PyCharm - 1.5 points
Sublime - 2 points

## Git integration

Both Sublime and PyCharm provide Git integration. PyCharm definitely comes out at the top here, with the ability to see exact diffs, and integrate external diff and merge tools.

![](http://i.imgur.com/KxTlFB2.png)


(Sublime)

![](http://i.imgur.com/wdczbrb.png?1)


(PyCharm)


Score:
PyCharm - 2 points
Sublime - 1 point

## Resource usage

### Energy usage

I use both Sublime and PyCharm on OSX, and OSX has nice Energy Impact information available in the Activity Monitor. Let’s take a look at that.

![](http://i.imgur.com/PQijxFE.png)


It seems that with my choice of plugins, Sublime has slightly higher energy usage compared to PyCharm. Almost all the plugins that I have installed in Sublime related to Python development are emulating some functionality that PyCharm already provides. Also, GitGutter and Anaconda are the only plugins which have always-running background processes that could elevate energy usage, and the functionality provided by them is present in PyCharm by default.

### Memory usage

There is a stark difference between memory consumption while idling between the two editors. While Sublime consumes ~50MB RAM when not in use, PyCharm chomps up 700MB.

![](http://i.imgur.com/2aj8NgH.png?1)
![](http://i.imgur.com/15jacdL.png)


Score:
PyCharm - 1 point
Sublime - 1 point

### Overall

Both Sublime and PyCharm have similar functionality, but PyCharm does most things better in comparison to Sublime. While Sublime Text is nagware with a $70 license fee, PyCharm CE is freeware, and PyCharm Professional Edition is priced at $99.

If you can spare $99 for a PyCharm Professional Edition license, it gets you some serious new features, like Flask/Django support, JS/HTML/CSS support, Database/SQL support, and more.

While points-wise, both tie at 7 points, I personally prefer PyCharm due to its superior built-in functionality, and I’m gonna stick with it.