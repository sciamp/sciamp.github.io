---
layout: post
title: "Soft pencil down approaching"
date: 2013-09-13 22:16
comments: true
categories: ['gnome', 'gsoc']
---

![sunset](/images/sunset.jpg)

Hi everybody! Soft pencil down is in two days and this week was violent bug fixing.  
I learned interesting thing about memory management (I have to thank [my mentor](http://blogs.gnome.org/cosimoc/) and this cool [post](http://tecnocode.co.uk/2013/09/03/const-gchar-vs-gchar-and-other-memory-management-stories/) that appeared some days ago on planet GNOME). Gnome Documents was crashing after quitting the presenter, as my smart mentor suggested me, too much g_object_unref :)
I fixed my CSS, now it isn't messing with Gnome Documents buttons background :)

<!-- More -->

So the presenter seems to be ready, as long as we do not find bugs :)
If you want to try it here is what you need to do:

* Build [evince](https://git.gnome.org/browse/evince) and [gnome-documents](https://git.gnome.org/browse/gnome-documents) (I suggest using [jhbuild](https://wiki.gnome.org/Jhbuild)).

* Be sure you can run a presentation from Documents.

* Get the code in branch develop in my [Evince](https://github.com/sciamp/evince-mirror/tree/develop) mirror and in my [Documents](https://github.com/sciamp/gnome-documents-mirror/tree/develop), compile Evince and then compile Documents.

* Plug a second monitor to your PC and then run gnome-documents and run a presentation.

There are some "off GSoC" things I really like to do in the near future:

* Discuss with Evince developers a way to use EvViewPresenter like in Documents, and implement it.

* Write an application to handle notes editing, instead of using Gedit (this will "hide" the JSON to the user, and will make the notes writing process easier).

* Slides preview on the presenter screen to jump quickly to a specific slide.

I'm having some problems recording screencasts, tomorrow I'll try again and post a demo here on the blog :)

Bye!
