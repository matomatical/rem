Matt's reMarkable
=================

Some files and notes about my remarkable.

For settings things up after an update, see [updating](updating.md).

Wishlist
--------

* some better file manager and offline backup.
  should just work with a normal file manager, or be even easier.
  * should be able to back up notebooks and pdf annotations, possibly in
    version control?
  * there was a custom cloud backup app somewhere.
  * git annex seems like the ideal eventual solution
* should be able to render them in SVG and HTML for loading online.


Existing Hacks
--------------

The fine folks at
[awesome-reMarkable](https://github.com/reHackable/awesome-reMarkable)
have a pretty big list of cool reM projects.
Here are some interesting ones (I don't think I have any resources that
are missing from that repo).

File system exploration:

* https://plasma.ninja/blog/devices/remarkable/2017/12/18/reMarkable-exporation.html
  * Notes about wifi settings and eduroam
  * same author as lines-are-beautiful

Lines format:

* https://plasma.ninja/blog/devices/remarkable/binary/format/2017/12/26/reMarkable-lines-file-format.html
  * breakdown of the file format
  * reference parser (/converter to svg or pdf) implemented in
    [C++](https://github.com/ax3l/lines-are-beautiful)
    and
    [rust](https://github.com/ax3l/lines-are-rusty)
* https://github.com/rschroll/rmrl
  * python module, command-line, converts .rm --> .pdf
  * same author as RCU (the paid suite)
  * run with `python -m rmrl [-h] <pages_directory> > page.pdf`
* I could make my own?

Screen sharing:

* `rmview`, an excellent screen-sharing application
  * https://github.com/bordaigorl/rmview
  * built with python

TODO: Look through the rest of the list

