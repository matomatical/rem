Example note
============

Today I created a single-page notebook and then copied the created files
off my tablet to explore them.

Directory structure
-------------------

The notebook files were found, all (presumably) in the one massive
directory, `.local/share/remarkable/xochitl/`.

Using `ls -lt | head -n10` I found the most-recently-modified files and they
look like they correspond to the notebook I just created.

```
.local/share/remarkable/xochitl/
├── b69969e2-d5e7-490d-b2b3-84507e26bf29
│   ├── 00e80220-1f00-4c75-9fd0-a501ee4bf2e3-metadata.json
│   └── 00e80220-1f00-4c75-9fd0-a501ee4bf2e3.rm
├── b69969e2-d5e7-490d-b2b3-84507e26bf29.content
├── b69969e2-d5e7-490d-b2b3-84507e26bf29.metadata
├── b69969e2-d5e7-490d-b2b3-84507e26bf29.pagedata
└── b69969e2-d5e7-490d-b2b3-84507e26bf29.thumbnails
    └── 00e80220-1f00-4c75-9fd0-a501ee4bf2e3.jpg
```

It appears that the directories contain a single file per notebook page
(the uuid of the page as per the metadata page list (see below) is the
same as the filenames in these directories).


Directory
---------

`00e80220-1f00-4c75-9fd0-a501ee4bf2e3-metadata.json` contains the following:

```
{
    "layers": [
        {
            "name": "Layer 1"
        }
    ]
}
```

OK, so this is where the layer names go (where do the layers themselves go?
all in the `.rm` file?)

`00e80220-1f00-4c75-9fd0-a501ee4bf2e3.rm` is a binary file, of size 20K.
The first few bytes are readable:

```
reMarkable .lines file, version=5
```

OK, so the versions probably change every time there is some kind of
software update that adds new brushes or other features.


Metadata
--------

`b69969e2-d5e7-490d-b2b3-84507e26bf29.content` is another json file:

```
{
    "coverPageNumber": -1,
    "documentMetadata": {
    },
    "dummyDocument": false,
    "extraMetadata": {
    },
    "fileType": "notebook",
    "fontName": "",
    "lineHeight": -1,
    "margins": 125,
    "orientation": "portrait",
    "pageCount": 1,
    "pages": [
        "00e80220-1f00-4c75-9fd0-a501ee4bf2e3"
    ],
    "textAlignment": "justify",
    "textScale": 1
}
```

`b69969e2-d5e7-490d-b2b3-84507e26bf29.metadata` is another json file:

```
{
    "deleted": false,
    "lastModified": "1627093025463",
    "lastOpenedPage": 0,
    "metadatamodified": false,
    "modified": false,
    "parent": "13ebedcc-a488-467a-bf4a-f0b4b193a12f",
    "pinned": false,
    "synced": false,
    "type": "DocumentType",
    "version": 0,
    "visibleName": "Testing"
}
```

`b69969e2-d5e7-490d-b2b3-84507e26bf29.pagedata` is a text file that contains
a single line:

```
Blank
```

This may be referring to the template which I have on the one page of this
document (the 'Blank' template).


Thumbnails
----------

`b69969e2-d5e7-490d-b2b3-84507e26bf29.thumbnails` is a directory containing
a single file, `00e80220-1f00-4c75-9fd0-a501ee4bf2e3.jpg`, which does indeed
contain a small rendering of the notebook's page. This has got to be the
thumbnail used in the page overview and the explorer.


Plan
----

If I was to come up with some programmatic tools to track, sync, and
interpret these notebooks, I wouldn't necessarily want to take on the
responsibility of maintaining compatibility with the filesystem and data
format for the long term.
I'd prefer something that *just works* and doesn't have to be revisited
after every update (it would be especially troubling if updating lead to
a loss of productivity while I find a way to reestablish control/access).

I could use the default tools, or someone else's tools, and accept their
limitations, but that's frustrating! Not to mention I will be reliant on
their support---this seems like an area in which I could be self-reliant.
(haha why do I always want to be self-reliant?)

The solution seems to be a kind of minimal dependence on the changing format.
For example, I should limit the conversions and manual hackery

* Interact with the device in the following essentially pull-only mode

Note: I do have the decision of whether or not to install each update,
so I would at least be able to consider that tradeoff at the time. But
still, ideally, I get new features *and* old custom features with little
delay.


Questions
---------

Notebooks:

1. Is it possible to manually insert new files? How much of the metadata
   does one have to provide?

2. How stable is the format over updates?

   * According to the lines-are-rusy implementation, it looks like the
     previous format (version=3) was not very different.



Other:

1. What do folders look like?

2. What do pdf documents look like?


References
----------

* The author of [`lines-are-beautiful`][lines repo] documented a lot of this
  exploration in the repo, a blog, and some recorded talks.

  [lines repo]: https://github.com/ax3l/lines-are-beautiful
