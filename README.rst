collective.simplewiki
=====================

Provides simple wiki-style linking to other content within the site.

Text that is wrapped with `(())` or `[[]]` is rendered as a link.

The wrapped text is used to look up content items within the site, as either ID or title.

If the content item exists on the site, the rendered link is to that item.

The link is resolved in the following order:

1. a matching ID within the same folder
2. a matching title within the same folder
3. a matching ID somewhere else in the site
4. a matching title somewhere else in the site

If none of these match (i.e., a content item by that ID or title does not exist), the rendered link is to the add form for a page ("Document" content type), with the Title field pre-filled with the text wrapped by `(())` or `[[]]`.

Example
-------

The following example shows how text is rendered on a new local Plone site named "Wiki" containing the default welcome page (ID: front-page, title: "Welcome to Plone")

The text::

  This is a link to a ((test page)).

  Whatever you do, don't [[try this at home]]!

  If in doubt, link to ((front-page)) or to ((front page)) or to [[Welcome!]] or [[Welcome]] or [[Welcome to Plone]].

is rendered as:

.. code-block:: html

  <div class="simplewiki-container">
    <p>This is a link to a 
      <a href="http://localhost:8080/Wiki/++add++Document?form.widgets.IShortName.id=test page&amp;form.widgets.IDublinCore.title=test page" title="Create missing content">+ test page</a>.
    </p>
    <p>Whatever you do, don't 
      <a href="http://localhost:8080/Wiki/++add++Document?form.widgets.IShortName.id=try this at home&amp;form.widgets.IDublinCore.title=try this at home" title="Create missing content">+ try this at home</a>!
    </p>
    <p>If in doubt, link to 
      <a href="http://localhost:8080/Wiki/front-page" title="Welcome to Plone">Welcome to Plone</a> or to 
      <a href="http://localhost:8080/Wiki/++add++Document?form.widgets.IShortName.id=front page&amp;form.widgets.IDublinCore.title=front page" title="Create missing content">+ front page</a> or to 
      <a href="http://localhost:8080/Wiki/front-page" title="Welcome to Plone">Welcome to Plone</a> or 
      <a href="http://localhost:8080/Wiki/front-page" title="Welcome to Plone">Welcome to Plone</a> or 
      <a href="http://localhost:8080/Wiki/front-page" title="Welcome to Plone">Welcome to Plone</a>.
    </p>
  </div>

Comments:

- The entire rich text field is wrapped in a `<div>` with the class `simplewiki-container`.
- `((test page))` links to an add form.
- `[[try this at home]]` links to an add form because no content item exists by that ID or title on the site.
- `((front-page))` links to the site's default front page.
- `((front page))` links to an add form because no content item exists by that ID or title on the site.
- All these link to the site's default front page because they match by title: `[[Welcome!]]`, `[[Welcome]]`, `[[Welcome to Plone]]`
  

Acknowledgements
----------------

This add-on was developed by `Wildcard Corp.`_ and graciously funded and released to the community by `Zombie Orpheus Entertainment`_.

Thanks to Ben Dobyns of Zombie Orpheus Entertainment and Hawke Robinson of `RPG Research`_

.. _Wildcard Corp.: https://wildcardcorp.com
.. _Zombie Orpheus Entertainment: http://zombieorpheus.com
.. _RPG Research: http://rpgresearch.com/






