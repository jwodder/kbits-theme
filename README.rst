This is the `Pelican <https://getpelican.com/>`_ theme for my blog `"Knowledge
Bits" <https://jwodder.github.io/kbits/>`_, split off into a separate
repository so that it can be reused by others.  The theme is a mixture of
similar styles from various sources, mostly the styles GitHub uses to render
markup.

A demo of the theme in action, designed to show off as many features & styles
as possible, can be found at <https://jwodder.github.io/kbits-theme-demo/>.


Features
========

- Article metadata (posted date, last modified date, authors, category, tags,
  translations, and any custom fields you specify) is displayed in a nice table
  underneath the article title

- Links to articles' source on GitHub can optionally be added to metadata
  listings

- You can add arbitrary lists of links to the navigation pane, not just "Links"
  and "Social"

- There is CSS support for the Docutils/reStructuredText table classes
  "booktabs" and "borderless" as well as for left-aligned, centered, and
  right-aligned tables

- Colorful reStructuredText admonitions, topics, and sidebars

- Strings are HTML-escaped where necessary, so you can safely put angle
  brackets in your article titles, categories, and tags

- ``MENUITEMS`` accepts relative URLs and automatically prepends ``SITEURL`` to
  them

- Support for specifying a favicon

- Support for the autopages_ plugin

- If you've disabled author pages by setting both ``AUTHOR_SAVE_AS`` and
  ``AUTHOR_URL`` to ``None`` or the empty string, then author names will not be
  hyperlinked.

- MathJax can be automatically enabled on every page

.. _autopages:
   https://github.com/getpelican/pelican-plugins/tree/master/autopages


Theme Settings
==============

kbits-theme recognizes the following theme settings:

``MENU_NAME``
   The name to display above the main menu on the navigation pane.  Defaults to
   no name.

``MENUITEMS``
   A list of (Title, URL) pairs for additional menu items to appear at the
   beginning of the main menu in the navigation pane.  If a given URL is
   relative (does not begin with either ``http://`` or ``https://``), then
   ``{{SITEURL}}/`` is prepended to it.  This allows you to link to locations
   on your site without having to give the full URL.

``PAGES_MENU = False``
   If true, pages will be given their own menu in the navigation pane,
   after the main menu but before the categories menu and any menus defined
   with ``EXTRA_MENUS``.

``PAGES_MENU_NAME = "Pages"``
   The name to display above the pages menu (if there is one) on the
   navigation pane

``CATEGORIES_MENU = False``
   If true, categories will be given their own menu in the navigation pane,
   after the main menu and pages menu but before any menus defined with
   ``EXTRA_MENUS``.

``CATEGORIES_MENU_NAME = "Categories"``
   The name to display above the categories menu (if there is one) on the
   navigation pane

``EXTRA_MENUS``
   A list of (Menu Name, Link List) pairs defining extra lists of links to add
   to the navigation pane beneath all other menus.  Each "Link List" is a
   sublist of (Link Name, Link URL) pairs.

   If a given link URL is relative (does not begin with either ``http://`` or
   ``https://``), then ``{{SITEURL}}/`` is prepended to it.  This allows you to
   link to locations on your site without having to give the full URL.

   For example, the following setting:

   .. code:: python

       EXTRA_MENUS = [
           ('Social', [
               ('My Twitter', 'https://twitter.com/…'),
               ('My Mastodon', 'https://…'),
               ('My GitHub', 'https://github.com/…'),
           ]),
           ('Favorite Tags', [
               ('Python', 'tags/python.html'),
               ('Pelican', 'tags/pelican.html'),
           ]),
       ]

   causes the following to be added to the navigation pane on the left of the
   page::

        Social
        * My Twitter
        * My Mastodon
        * My GitHub

        Favorite Tags
        * Python
        * Pelican

``SITESUBTITLE``
   A subtitle to appear in the header

``FOOTER_HTML``
   HTML to display at the bottom of every page, centered and in small font.

``GITHUB_SOURCE_URL``
   If your site's repository is hosted on GitHub, setting this variable to the
   repository's URL (in the form ``"https://github.com/$OWNER/$REPO"``, without
   trailing ``.git``) will add a "Page Source" entry to each article's metadata
   table pointing to the article source file on GitHub.  Setting this value
   also requires setting ``PATH_IN_REPO``.

``GITHUB_SOURCE_BRANCH = "master"``
   The branch of the ``GITHUB_SOURCE_URL`` repository on which the site's
   source is located.

``PATH_IN_REPO``
   The ``/``-separated path to your content directory, relative to the root of
   your repository.  This will usually be equal to ``PATH``.  This needs to be
   set whenever ``GITHUB_SOURCE_URL`` is set.

``FAVICON_URL``
   A URL pointing to an image to use as the site's favicon.  If the URL is
   relative (does not begin with either ``http://`` or ``https://``), then
   ``{{SITEURL}}/`` is prepended to it.

``FAVICON_TYPE``
   The MIME type of your site's favicon

``SHOW_AUTHOR = True``
   Whether to show articles' authors in the metadata table

``SHOW_AUTHOR_IN_LISTINGS = True``
   Whether to show articles' authors in article listings (``index.html`` etc.)

``USE_MATHJAX = False``
   Whether to enable MathJax on every page of the site

``MATHJAX_SCRIPT = "https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"``
   The MathJax script to load

``MATHJAX_CONFIG = {}``
   Configuration settings for MathJax.  Configuration is applied assuming
   version 3 of MathJax is in use.  Only JSON-serializable values are supported
   in ``MATHJAX_CONFIG``.

``EXTRA_METADATA_FIELDS``
   A list of (Field Name, Article Attribute) pairs specifying additional
   metadata fields to list in articles' metadata tables.  The "Field Name" is
   the text to label the field with in the table (minus the colon which will be
   automatically appended), and the "Article Attribute" is the name of the
   field as available as an attribute of an ``Article`` object (i.e., the name
   of the field as written in your document metadata, but converted to
   all-lowercase).  If a given field is empty or not set on an article, it is
   not listed in that article's metadata table.

   For example, if you include an "``:ORCID:``" field in the docinfo of your
   articles, you can include ``("Author ORCID", "orcid")`` in
   ``EXTRA_METADATA_FIELDS`` to cause the field to be listed in the metadata
   table with a label of "Author ORCID:".


Third-Party Assets
==================

This theme contains several assets taken or derived from third-party sources:

.. list-table::
    :header-rows: 1

    * - File
      - Source
      - License & Copyright
    * - ``static/css/admonitions.css``
      - `sphinx-rtd-theme <https://github.com/readthedocs/sphinx_rtd_theme>`_
      - Released under the MIT License.  Copyright (c) 2013-2018 Dave Snider,
        Read the Docs, Inc. & contributors
    * - ``static/css/blockquote.css``
      - <http://primer.style/css>
      - Released under MIT license. Copyright (c) 2019 GitHub Inc.
    * - ``static/css/docinfo-topics.css``
      - `Sphinx <https://www.sphinx-doc.org>`_
      - Released under the BSD license.  Copyright 2007-2020 by the Sphinx
        team.
    * - ``static/css/docutils.css``
      - `Docutils <https://docutils.sourceforge.io>`_, ``html4css1.css`` file
      - Public domain
    * - ``static/css/headers.css``
      - <http://primer.style/css>
      - Released under MIT license. Copyright (c) 2019 GitHub Inc.
    * - ``static/css/kbd.css``
      - <http://primer.style/css>
      - Released under MIT license. Copyright (c) 2019 GitHub Inc.
    * - ``static/css/sidebar.css``
      - `sphinx-rtd-theme <https://github.com/readthedocs/sphinx_rtd_theme>`_
      - Released under the MIT License.  Copyright (c) 2013-2018 Dave Snider,
        Read the Docs, Inc. & contributors
    * - ``static/css/table.css``
      - <http://primer.style/css>
      - Released under MIT license. Copyright (c) 2019 GitHub Inc.
    * - ``static/css/topic.css``
      - `pallets-sphinx-themes <https://github.com/pallets/pallets-sphinx-themes>`_
      - Released under the BSD 3-Clause license.  Copyright 2007 Pallets.
    * - ``static/images/rss.svg``
      - `Wikimedia Commons <https://commons.wikimedia.org>`_, `[link]
        <https://commons.wikimedia.org/wiki/File:Generic_Feed-icon.svg>`_
      - Released under the GNU GPL v2+, GNU LGPL v2.1+, and MPL 1.1
    * - ``static/fonts/BabelStoneShapes.{ttf,woff,woff2}``
      - `BabelStone Shapes <https://babelstone.co.uk/Fonts/Shapes.html>`_ v.
        13.0.1 by BabelStone
      - Released under the SIL Open Font License 1.1
