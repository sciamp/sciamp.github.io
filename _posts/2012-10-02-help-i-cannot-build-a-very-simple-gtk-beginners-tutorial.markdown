---
layout: post
title: "Help! I cannot build a very simple GTK beginner's tutorial!"
category: [fedora, fedora17, gnome, gtk, programming, pkg-config]
published: false
---

I ran into some trouble trying to access a gnome keyring secret
through [gir_ffi-gtk](https://github.com/mvz/gir_ffi-gtk) (I won't
talk about this! gir_ffi-gtk and my first ruby gem will be the next
post!) so I decided to stop for a while and try to do it with a little
c program.
I got a new project in [Anjuta](http://projects.gnome.org/anjuta/) and
compiled an empty file just to check if everything was ready to go

<!-- More -->

``` c
    #include <config.h>
    #include <gtk/gtk.h>


    int
    main (int argc, char *argv[])
    {
	    return 0;
    }
```    
**Boom!** 
    
    main.c:21:21: fatal error:gtk/gtk.h: No such file or directory
    
WTF? Of course I'm missing some packages,
[took advice](https://live.gnome.org/DeveloperTools/Installation/Fedora):

    sudo yum groupinstall development-libs development-tools
    gnome-software-development
    
    Loaded plugins: langpacks, presto, refresh-packagekit
    Warning: Group development-libs does not have any packages to install.
    Warning: Group development-tools does not have any packages to install.
    Warning: Group gnome-software-development does not have any packages to install.
    No packages in any requested group available to install or update

    
WTF? I am missing nothing! I decided to check the option passed to
gcc:

    ~  (ruby-1.9.3-p194) ᐅ pkg-config --cflags --libs gtk+-3.0
    Package x11 was not found in the pkg-config search path.
    Perhaps you should add the directory containing `x11.pc'
    to the PKG_CONFIG_PATH environment variable
    Package 'x11', required by 'Xrender', not found

Oh my gosh! I'm really missing something:

    ~  (ruby-1.9.3-p194) ᐅ locate x11.pc
    /usr/lib/pkgconfig/x11.pc

no I don't! Let's have a look to *PKG_CONFIG_PATH*:

    ~  (ruby-1.9.3-p194) ᐅ echo $PKG_CONFIG_PATH
    YES, I AM A BLANK LINE! :P

Got it! We just add *x11.pc* path:

    ~  (ruby-1.9.3-p194) ᐅ export PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/lib/pkgconfig 

We're done:

    ~  (ruby-1.9.3-p194) ᐅ pkg-config --cflags --libs gtk+-3.0
    -pthread -I/usr/include/gtk-3.0 -I/usr/include/pango-1.0
    -I/usr/include/gio-unix-2.0/ -I/usr/include/atk-1.0
    -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0
    -I/usr/include/freetype2 -I/usr/include/glib-2.0
    -I/usr/lib64/glib-2.0/include -I/usr/include/pixman-1
    -I/usr/include/libpng15  -lgtk-3 -lgdk-3 -latk-1.0 -lgio-2.0
    -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo-gobject -lpango-1.0 -lcairo
    -lgobject-2.0 -lglib-2.0

If you want to use Anjuta maybe you have to set *C preprocessor flags*
in the *Target properties* to *`pkg-config --cflags --libs gtk+-3.0`*,
if this is not enough you should also set the *PKG_CONFIG_PATH* as
above in *Build > Configure Project ...*.

Bye!
