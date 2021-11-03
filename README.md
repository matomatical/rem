Matt's reMarkable
=================

I now manage much of my life with the reMarkable paper tablet. When I'm not
on paper, I'm at home in a terminal emulator. I have neither time nor battery
life for gratuitous cloud connections and integrations. If you're like me,
you might find this repository interesting---here I document the family of
tools and scripts and so on that I use to manage my tablet.

Contents
--------

In this repository:

* [meta](meta/): Design and exploration notes while thinking about how to use
  the tablet.
* [skins](https://github.com/matomatical/reMarkable-customisation):
  My custom templates and splashscreens and instructions for creating and
  installing new ones.
* tools: A family of software tools I am gathering and building for managing
  my tablet.
  * (todo: list)
* README.md: You are here.

In this README:

* [TODO](#todo): Next steps.

* [Ideals](#ideals):
  The thing about open computer systems is that, typically, if one can
  imagine it, one can make it a reality.
  In this spirit, I'll think about the ideal workflows and tools and the
  goals to which I am trying to align them.

* [Links](#links):
  Useful links to other information sources and projects relevant to the
  management of my tablet.


TODO
----

* Flesh out list of tools in contents.
* Build more tools (add a dedicated 'Ideas' section?)
  * A system for offline backup/version control of notebooks and annotations.
  * A script for automatically installing templates and splashscreens.
  * A system for leveraging storage by loading/unloading PDFs.
* Update update checklist.
* Add or find a guide to installing SSH keys to the device.
* Flesh out 'Ideals' section.
* Add more links. Look through the rest of the awesome list for inspiration.

Ideals
------

**Offline use:**

TODO: Write about how I hope to manage without relying on the cloud services
(but still should feel free to use the cloud services). From using the USB
connection to load files to making my own backup and version control system,
and my own system for loading/unloading PDFs to make space.

**Updating:**

The reMarkable tablet's software continues to progressively improve. A
number of features that were lacking when I first got the tablet have now
been provided (e.g. better selection, quick switching to recent documents,
persistent pen settings).

At this stage, I plan to stay on the main line of official software rather
than install custom launchers. This could change in the future if custom
launchers look more appealing, or official software stagnates, or I get more
time to look into custom launchers.

Frequent updates threaten to create additional work maintaining custom tools
and configuration on the device. Hopefully major changes to formats (e.g.
the .rm binary file format or the flat filesystem structure) are rare;
otherwise I will ideall maintain a list of all of the reinstallation steps
that are required after each update, and make this process as streamlined as
possible.

(TODO: update and link to 'update checklist' from meta).

**Sharing:**

It's useful to be able to share the screen of the reMarkable during meetings
and lectures, as an effective digital whiteboard.
[rmview](https://github.com/bordaigorl/rmview) is really great for this so
far. It's super straightforward to connect to, too.
The v2.9 update forcing an extra step of opening screen-sharing on the device
is unwelcome. Is there a workaround? Can I leave it always on?

It's useful to be able to share or publish handwritten notes and diagrams
in PDF, PNG, or SVG formats.
I should ideally have some very streamlined process for generating these
files from notes on the device, and even tracking them in public
repositories (SVG for example is a good text format for version control,
if generated sensibly).


Links
-----

This repository is not affiliated with Remarkable AS. I'm just a happy user.
Here is a collection of other third-party links and tools.

Communities:

* [awesome-reMarkable](https://github.com/reHackable/awesome-reMarkable)
  collates most of the reM projects I am aware of. Plenty of other options
  there if you're looking for something different.
* There is a wiki with lots of software configuration information and
  third-party hardware advice (e.g. custom pens and cases).
  TODO: Add link.
* There is a subreddit and a discord server. I don't really go there...

Reverse engineering by [Axel Hübl](https://plasma.ninja/blog/about/):

* File system exploration
  https://plasma.ninja/blog/devices/remarkable/2017/12/18/reMarkable-exporation.html
  * plus, some helpful notes about wifi and eduroam
* Lines format breakdown
  https://plasma.ninja/blog/devices/remarkable/binary/format/2017/12/26/reMarkable-lines-file-format.html
  * breakdown of the file format
  * reference parser (/converter to svg or pdf) implemented in
    [C++](https://github.com/ax3l/lines-are-beautiful)
    and [rust](https://github.com/ax3l/lines-are-rusty)

Hardware and software hacks from [Davis Remmel](http://www.davisr.me/):

* A hardware project to install an exeternal microSD card
  http://www.davisr.me/projects/remarkable-microsd/
  * inspirational
* A paid manager application http://www.davisr.me/projects/rcu/
  * I don't use this but it's impressive

FUSE for reMarkable cloud by [Robert Schroll](http://rschroll.github.io/):

* Python-implemented FUSE filesystem on top of reMarkable cloud
  https://github.com/rschroll/rmfuse
  * built atop own cloud library (https://github.com/rschroll/rmcl)
    (forked from rmapy https://github.com/subutux/rmapy).
  * and own .rm to .pdf converter (https://github.com/rschroll/rmrl)
  * I don't want to use the coud but this could be good inspiration for
    a FUSE system to access the files on the device itself.
* The converter is also a standalone python program 
  * run with `python -m rmrl [-h] <pages_directory> > page.pdf`
  * I don't want to use python and I want more formats (namely svg) but
    this could be a good starting point for my own converter.

Screen sharing:

* `rmview`, an excellent screen-sharing application
  https://github.com/bordaigorl/rmview
  * built with python
  * I use this

Other/unsorted:

* Look through awesome list for more inspiration
* There was a custom cloud backup app somewhere; that could be interesting
  to investigate, but I am happy enough with low dependence on remarkable's
  cloud right now, and it seemed like it would be kinda dangerous to try
  setting up something custom.
* https://github.com/LinusCDE/rmWebUiTools + rsync + git annex etc?
* https://github.com/after-eight/regitable
