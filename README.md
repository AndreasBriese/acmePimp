---
__acmePimp__
=============
---

acmePimp is my personal pimp of Rob Pike's great acme editor (or to be more concrete: Russ Cox's plan9port of acme).

NOTE: acmePimp is tested for OSX only !

what is this?

![screenshot of acmePimp: screenshot.png](./screenshot.png?raw=true "acmePimp screenshot")

when first tried out acme didn't really liked it for

    - use with missing 3 button mouse on MBP
    - contra intuitive use of the arrow UP- & DOWN- keys
    - it's color layout (there is a narrative about the pastel colors - i know)
        -> i got the principal color changes from the web, but i can't find the link again?
    - no go autocompletion
        -> solved using "agoc" https://github.com/s-urbaniak/agoc which shows me possible completions (and the definitions!) of https://github.com/nsf/gocode in a separate window

on the first i adapted and actually don't need chording.

on the second i found that i have a problem primary with the UP key as i use to open-close brackets left-arrow-enter-enter-up-arrow when starting a function or the like. Later found the i ofetn use the DOWN key involuntary - or for it's "natural purpose".

with this commit all arrows move the cursor: 

* UP - end of the pevious line
* DOWN - next line same vertical position or end-of-line if the line is shorter than it's predecessor. 

last commits include the usual CMD+'s' for saving and auto parenthesis closing addition for opening '(', '{' and "[".

that is edited within _text.c_ in the acme folder (search for /*me*/ for the changes) and up-arrow will now jump up to the line end of the previous line.

for acme (_acme.c_) the tab indention is default now and (proportional) default font is set to /mnt/font/Menlo-Regular/14a/font (search "/*me*/" in acme.c for the changes in the source code)

call acme -o ... to use acme's original color mode (acme -a .. does set off auto indention) 

make sure you compiled plan9/src/cmd/fontsrv to access OSX fonts; list of fonts:

    $ cd /usr/local/plan9/src/cmd/fontsrv
    $ fontsrv -p .



---

installation:

clone or download this repo

    cd </into-the-downloaded-repo/>
    // backup the original acme folder
    $ mv /usr/local/plan9/src/cmd/acme /usr/local/plan9/src/cmd/_acme.bup
    $ mv acme /usr/local/plan9/src/cmd/acme
    $ cd /usr/local/plan9/src/cmd/acme
    $ 9 mk install
