---
layout: post
title: "GSoC final report"
date: 2013-09-23 15:58
comments: true
categories: ['gnome', 'gsoc']
---

I really don't know how to start this, I feel like there are so many things to say, but I'll stick to technical stuff, I'll just say that I love you all and that learning to move my first steps in GNOME was awesome. Thanks for everything.

<!-- More -->

Well, this morning I fixed the last two (known) bugs, and I'm happy to show you extra GSoC stuff:

* When running a presentation without notes, there's a big empty portion of the presenter screen. We didn't like it and of course could happen that someone wants to present without notes, so we decided to use this empty space to display current and next slides. Here is the result:

![withNotes](/images/with_notes.png)

while if we're presenting without notes

![withoutNotes](/images/without_notes.png)

I think this could be useful. I mean some people love to have "lightweight slides", in this case notes could be very helpful, but if for some reason you do not want/need notes you'll see bigger slides on the presenter screen!

* As I wrote in my previous post, it'd be nice to have an application for editing notes. Well I started writing one

![notesEditor](/images/note_editor.png)

Basic functions are working (you can edit and save a note file) but there's a lot of work to do like providing basic text formatting, undo/redo..  
I need an icon for this and a GNOMEish design :) (help me!). As usual you can find the source code of the note editor on my [github](https://github.com/sciamp/note-editor).

What I plan to do in the near future is hunting bugs on the presenter and ear some feedback about it from you, so I can start to improve it; and finishing to write the note editor hoping it will be useful.

See ya!

By the way I'm sorry for the screencast I promised in my last post, it's like I cannot record screencasts if I attach a second monitor, and of course I cannot show my work without a second monitor :/
