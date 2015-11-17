---
layout: post
title: "EvViewPresenter: ready, set, go!"
date: 2013-06-28 18:40
comments: true
categories: [gnome, GSoC, google, summer, code]
---

Hi! This is the first update about my GSoC.

As this is the first post since I'm on
[planet gnome](http://planet.gnome.org) (thanks
[Alberto](https://wiki.gnome.org/AlbertoRuiz)!), if you want to know
more about my GSoC project you can read my
[previous post](/blog/2013/06/03/gsoc-2013/), you also find some links
on the
[gnome live page](https://wiki.gnome.org/SummerOfCode2013/Projects/AlessandroCampagni_DualScreen).

<!-- More -->

After some [warm up code](https://github.com/sciamp/GSoC2103_warm_up_session) to
better understand the connections between some evince components
(EvDocument, EvDocumentModel and EvViewPresentation) I started coding
the EvViewPresenter class (in the
[evince libview](https://developer.gnome.org/libevview/unstable/)).

Let's review the mockup to show the main idea:

![GSoC main idea](/images/idea.png)

Of course in the real life we can take advantage of the typical laptop
screen ratio (16:9) saving a lot of space for annotations:

![first](/images/first.png)

![second](/images/second.png)

These are two (consecutive) screenshots of the
[latest progress](https://github.com/sciamp/evince-mirror/blob/4d17657167423bb568ea3ccd8c7972aa057bf0e1/libview/ev-view-presenter.c).
You can see the current slide on the top left and the next slide on
the bottom left of the widget.

The EvViewPresenter class is nothing more than a GtkWidget with the
current and the next page rendered through
[EvJob](https://developer.gnome.org/libevview/unstable/EvJob.html).

Stay tuned!
