---
layout: post
title: "Where were we? (EvViewPresenter updates from a lazy blogger)"
date: 2013-08-29 21:44
comments: true
categories: ['gnome', 'gsoc']
---

It's been a long time since <del>I Rock and Rolled</del> my last
update, I'm *sorry* :( (I really am).  
I'm afraid this is going to be a bit long, I'll talk about my GSoC
project status and about what led us to some choices we made about the
way we edit preseter notes.

![RockNRoll](/images/rockandroll.jpg)

<!-- More -->

But first I'd like to say something else about GUADEC (as I forgot
to publish the blog post I was writing in Vienna while waiting at the
airport). I really had a great time there and I really enjoyed every
single word, smile, walk, beer I shared with everyone of you: thank
you! Of course thanks to everyone involved at any level in the
organization, I felt like I belong to something - in my humble
opinion - this is one of the most warm and comforting feeling. I truly
hope to have the opportunity to attend the next one.

### Presenter notes
The first idea we had about the presenter notes was a JSON file

``` json
{
  ...
  "n" : "these are the notes for the n-th slide",
  "n+1" : "yes these are the notes for the (n+1)-th slide :)",
  ...
}
```
[This is easy to handle](https://wiki.gnome.org/JsonGlib) and look
like a good way to achive our goal. So we started thinking about a way
to edit these notes. The first question we asked ourselves was "Who
should handle the notes editing?". We initially thought about having a
widget inside Documents for editing the notes, but after a talk on
the Evince channel on IRC and a chat with Allan while walking to the
venue on an insanely hot morning in Brno we realized that Evince and
Documents are tools for viewing documents, not for editing.  
Long story short, when we ask Documents to edit the notes Gedit is
launched with the notes file opened. And this is how and where we
create a notes file: if you want to edit the notes file for the local
document */home/usernamehere/Documents/presentation.pdf* we're going
to look for */home/usernamehere/Documents/presentation.pdf.notes* and
we're going to create it if it doesn't exist. If the documents is
remote (e.g. Google Drive) or a LibreOffice document we're going to
cache the document
*/home/usernamehere/.cache/gnome-documents/gnome-documents-3191238210.pdf*
and edit
*/home/usernamehere/.cache/gnome-documents/gnome-documents-3191238210.pdf.notes*.  
Maybe in the future (i.e. after GSoC is over) we can think about
having a specific application (outside Evince and Documents) for
handling the presenter notes editing (I'm thinking about an
application that shows the slide and an input for the notes, buttons
for saving, basic formatting, and so on..) but this will not be in my
GSoC project. I don't know, but maybe we would like to have a
"presentation" format: a sort of archive that contains the
presentation and the document...don't know, just some random ideas :)

### EvViewPresenter status

I'm pretty happy with my latest progresses. We've got the global timer,
there's some room to place a "current slide" timer. The former can be
started and paused with a button, the latter is automatically started
as you change slide. We decided to use a timer instead of a countdown,
because a countdown implies asking the user how many time there's for
the presentation, how many time for each slide.
Some issues about keyboard events caught by the TextView were fixed.
We're thinking about making the current slide bigger than the next
one, so it's easier to understand on the presenter view which one is
the current slide!

That's all for now, stay tuned!
