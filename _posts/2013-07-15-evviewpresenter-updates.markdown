---
layout: post
title: "EvViewPresenter updates"
date: 2013-07-15 20:11
comments: true
categories: [GSoC, gnome]
---

Hi everybody! About two weeks ago I showed you the very first steps of
the presenter view. Some things have changed and other things have been
improved, still some bugs around though!

<!-- More -->

* No more segmentation fault when reaching the end of presentation,
  while the presentation displays a black screen with "End of
  presentation, press ESC..." the same happens on the presenter view.

* Found the cause of the bug responsible for not updating the next
  slide under certain conditions. Not yet pushed, but fixed!

* EvViewPresenter is now built upon an EvViewPresentation
  and holds a reference to it.
  This seems the best compromise between reusing as much as we can existing
  code and keep EvViewPresentation independent from the presenter. We
  can also read the state from the presentation (through some
  "private" getter available from the presenter in
  ev-view-presentation-private.h), and connect a callback to the
  *notify::current-page* signal emitted by the presentation when the
  displayed page changes (this is very useful to keep the presenter
  synchronized with the presentation). On the "theoretical" side it
  sounds fair that we cannot have a presenter view without a
  presentation :)
  {% highlight c %}
  GtkWidget *ev_view_presenter_new (EvViewPresentation *presentation);
  {% endhighlight %}

* I started talking with my mentor about presenter notes, we took a
  look at PDF annotations (that are supported in evince) but we found
  out some issues: as their name says they only work with PDFs, while
  evince (and hence gnome-documents) can deal with lots of different
  file formats (i.e. we can run a presentation with something that is not a PDF);
  each PDF annotation is bound to a specific point of the page, they
  don't look like the right tool for our goal.
  This lead us to think about a "separate file solution": but in spite
  of using *ad hoc* PDF (or PS, DVI, whatever) file with the same
  number of page of the presentation, that should be written - I guess -
  by the presenter (not the widget, the presenter in the flesh!) with,
  perhaps, the same tool she/he used to write his presentation, we
  think it would be better and more natural to edit the presenter notes within evince
  or gnome-documents and store them in a JSON file (yes, one JSON file
  for each presentation) somewhere. I believe presenter notes should
  have their own blog post, so I'm stop talking about it!

* Lastly some words about what EvViewPresenter should be. Right now
  we're building a widget (like in EvViewPresentation), this lead us
  to the question "How and Where should I place the notes?". For the
  sake of simplicity we do not want the client code to worry about
  this, hence we're going to deliver a GtkWindow with all the
  widgets (the presenter view, the presenter notes and gadgets) packed
  in it, so the client application should only call the new method and
  fullscreen the window.

Thanks for reading :)
