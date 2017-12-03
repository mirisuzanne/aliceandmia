public: yes
image:
  - src: 'podcast/e001/cover.jpg'
summary: |
  This is a sample document
  for understanding how our static-site
  generator works, and how to write posts.
  This "summary" section will appear on post-list pages,
  and be used as the large-text intro paragraph
  on post-detail pages.


*******************
Sample RST Document
*******************

`RST`_ is a document format
for writing rich text in a plain text file.
Line-breaks will be ignored,
and I like to keep lines broken apart
roughly by phrase.
Paragraph breaks are created using an empty line.

.. _RST: http://docutils.sourceforge.net/docs/user/rst/quickref.html

This will start a new paragraph.
I can also add lists and other formatting:

- Use ``*italic text*`` to create *italic text*.
- Use ``**bold text**`` to create **bold text**.

Links can be added in the following format:

::

  Lorem ipsum dolor sit amet,
  consectetur adipisicing elit,
  `this will be a link`_
  sed do eiusmod tempor incididunt
  ut labore et dolore magna aliqua.

  .. _this will be a link: http://example.com


Document MetaData
=================

Each ``.rst`` file in this ``content`` folder
represents a page on the site.
Pages that are nested inside ``year/month/day`` folders
are treated as blog-posts
to be listed on the home page and tag-pages
(e.g. "Podcast" or "Twined Fragments").

The top part of the file includes page metadata
in `YAML`_ format:

.. _YAML: https://learn.getgrav.org/advanced/yaml

::

  public: yes
  tags: ['Writing', 'Twined Fragments']
  image:
    - src: 'podcast/e001/cover.jpg'
  elsewhere:
    - url: https://psiloveyou.xyz/twined-fragments-sex-love-romance-c292698d8f1a
      src: 'PS I Love You'
  mp3: 'feeds.soundcloud.com/stream/364275896-aliceandmia-s1-episode-01-introducing-alice-mia-and-the-landscape-of-gender.mp3'
  summary: |
    “A few months into my gender transition
    I’m living full-time as a woman.
    I don’t have many guy friends, but my guitarist is one.
    Parting, I lean in for the cheek-kiss
    but he plants a good one right on my lips.
    His wife raises an amused eyebrow,
    *Ha, well, I guess you two get to do that now.*”

1. **public**: all posts are live on the site,
   if you know the proper url,
   but "public" posts appear in the list.
   This allows you to create drafts
   by making them with ``public: no``.

2. **tags** are only allowed on posts
   in the date-specific folders.
   At this point we're using tags
   to distinguish between ``Writing`` and ``Podcast``,
   or to assign posts to a particular series,
   such as ``Twined Fragments``.
   We can add more tags as we see fit.

3. **image**: The main image for the page.
   Only the ``src`` value is required --
   relative to the ``content/static/images/`` directory --
   though ``alt`` is also accepted.

4. **elsewhere** allows us to create links to content
   that we are hosting somewhere else (e.g. Medium).
   This requires both a ``src`` name and ``url``.

5. **mp3** is only required for posts with embeded audio or video,
   e.g. podcast episodes.
   See "Embeded Audio/Video Players" section below.

6. **summary** text should start with a ``|``
   and have a short paragraph of content
   indented below, in RST format.
   The summary will be used on list pages,
   and at the top of a post detail page.


Document Structure
==================

The YAML metadata must be at the top of each page,
though not all fields are required.
Following the metadata,
there should be **two empty lines**
followed by the page title.
Page titles look like this:

::

  *****************
  Sample Page Title
  *****************

Below the page title,
the rest of the document is plain RST.
Sub-headings can be added
to break up the page:

::

  Second Level Heading
  ====================

  Third Level Heading
  -------------------

  Fourth Level Heading
  ~~~~~~~~~~~~~~~~~~~~

For unknown reasons,
any heading that comes immediately after the page title
will be removed.
It's a dumb limitation.

you can also create ``& & &`` section-breaks
by adding a horizontal rule (``------``)
as a paragraph alone between sections:

::

  Lorem ipsum dolor sit amet,
  consectetur adipisicing elit…

  ------

  Duis aute irure dolor in reprehenderit
  in voluptate velit esse
  cillum dolore eu fugiat nulla pariatur.


Audio/Video & Images
====================

Images
------

Images can be added in RST:

::

  .. callmacro:: av.macros.j2#image
    :src: 'podcast/e001/bria.jpg'
    :alt: 'describe the image for non-sighted users'
    :link: 'https://www.facebook.com/BriaComics/'

    This is the visible caption of the figure,
    using RST as needed.

Unless we are linking an image
on someone elses site (which is risky),
our image ``src`` paths are always relative to the
``content/static/images/`` directory.
All our images will be added to that folder.
The ``:size:`` attribute
accepts ``full`` --
the default, for full-width images --
or ``left``/``right`` for images
small enough to float beside content.


Embeded Audio/Video Players
---------------------------

To embed audio or video,
like an episode of the podcast,
start by adding an ``mp3`` configuration
to the YAML metadata.
This should include the full link to an mp3 file
(with `http://` removed).
This should be provided by the SoundCloud rss feed.
That will provide the audio to social media sites.

To embed the audio/video in the page itself,
use the following embed code:

::

  .. callmacro:: av.macros.j2#embed
    :src: '<iframe width="100%" height="166" scrolling="no" frameborder="no" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/364275896&amp;color=%23ac0056&amp;auto_play=false&amp;hide_related=false&amp;show_comments=true&amp;show_user=true&amp;show_reposts=false&amp;show_teaser=true&amp;visual=true"></iframe>'

    You can add an optional caption below.

If no caption is given,
set ``:caption: none``:

::

  .. callmacro:: av.macros.j2#embed
    :src: '<iframe width="100%" height="166" scrolling="no" frameborder="no" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/364275896&amp;color=%23ac0056&amp;auto_play=false&amp;hide_related=false&amp;show_comments=true&amp;show_user=true&amp;show_reposts=false&amp;show_teaser=true&amp;visual=true"></iframe>'
    :caption: none
