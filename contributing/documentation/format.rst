Oblika dokumentacije
====================

Symfony2 dokumentacija uporablja `reStructuredText`_ kot njen označevalni jezik in
`Sphinx`_ za gradnjo izpisa (HTML, PDF, ...).

reStructuredText
----------------

reStructuredText *"je enostavna za branje, what-you-see-is-what-you-get enostavna tekstovna
označevalna sintaksa in prevajalni sistem"*.

Več o njegovi sintaksi se lahko naučite z branjem obstoječih Symfony `dokumentov`_
ali z branjem `reStructuredText Primer`_ na Sphinx spletni strani.

.. caution::

    Če ste seznanjeni s t.i. Markdown-om, bodite pazljivi, saj so stvari včasih zelo
    podobne vendar drugačne:

    * Seznami se začnejo na začetku vrstice (indentacija ni dovoljena);
    * Medvrstični bloki kode uporabljajo dvojne črtice (````na primer tako````).

Sphinx
------

Sphinx je gradilni sistem, ki doda nekaj lepih orodij za izdelavo dokumentacije
iz reStructuredText dokumentov. Kot tak, dodaja nove direktive in
tolmačene tekstovne vloge za standardizacijo reST `označevanja`_.

Obarvanje sintakse
~~~~~~~~~~~~~~~~~~

Vsi primeri kode uporabljajo PHP kot privzeti označevalni jezik. To lahko spremenite
s ``code-block`` direktivo:

.. code-block:: rst

    .. code-block:: yaml

        { foo: bar, bar: { foo: bar, bar: baz } }

Če se vaša PHP koda začne s ``<?php``, potem potrebujete uporabiti ``html+php`` kot
označevalni psevdo jezik:

.. code-block:: rst

    .. code-block:: html+php

        <?php echo $this->foobar(); ?>

.. note::

    Seznam podprtih jezikov je na voljo na `Pygments spletni strani`_.

.. _docs-configuration-blocks:

Nastavitveni bloki
~~~~~~~~~~~~~~~~~~

Kadarkoli prikažete nastavitve, morate uporabiti ``configuration-block``
direktivo za prikaz nastavitev v vseh podprtih nastavitvenih formatih
(``PHP``, ``YAML``, in ``XML``)

.. code-block:: rst

    .. configuration-block::

        .. code-block:: yaml

            # Configuration in YAML

        .. code-block:: xml

            <!-- Configuration in XML -->

        .. code-block:: php

            // Configuration in PHP

Prejšnji reST odrezek se izpiše sledeče:

.. configuration-block::

    .. code-block:: yaml

        # Configuration in YAML

    .. code-block:: xml

        <!-- Configuration in XML -->

    .. code-block:: php

        // Configuration in PHP

Trenutni seznam podprtih formatov je sledeči:

===============  ==================
Format oblike    Prikazano
===============  ==================
html             HTML
xml              XML
php              PHP
yaml             YAML
jinja            Twig
html+jinja       Twig
html+php         PHP
ini              INI
php-annotations  Anotacije
php-standalone   Samostojna uporaba
php-symfony      Uporaba ogrodja
===============  ===================

Dodajanje povezav
~~~~~~~~~~~~~~~~~

Da dodate povezave na druge strani v dokumentih uporabite sledečo sintakso:

.. code-block:: rst

    :doc:`/path/to/page`

Uporaba poti in imena datoteke strani brez končnice, na primer:

.. code-block:: rst

    :doc:`/book/controller`

    :doc:`/components/event_dispatcher/introduction`

    :doc:`/cookbook/configuration/environments`

Tekst povezave bo glavni naslov dokumenta, na katerega se povezuje. Lahko
tudi določite alternativni tekst za povezavo:

.. code-block:: rst

    :doc:`Spooling Email </cookbook/email/spool>`

Lahko tudi dodate povezave k API dokumentaciji:

.. code-block:: rst

    :namespace:`Symfony\\Component\\BrowserKit`

    :class:`Symfony\\Component\\Routing\\Matcher\\ApacheUrlMatcher`

    :method:`Symfony\\Component\\HttpKernel\\Bundle\\Bundle::build`

in k PHP dokumentaciji:

.. code-block:: rst

    :phpclass:`SimpleXMLElement`

    :phpmethod:`DateTime::createFromFormat`

    :phpfunction:`iterator_to_array`

Testiranje dokumentacije
~~~~~~~~~~~~~~~~~~~~~~~~

Za testiranje dokumentacije preden pošiljate:

* Namestite `Sphinx`_;
* Namestite razširitve Sphinx z uporabo git podmodulov: ``git submodule update --init``;
* (Opcijsko) Namestite paket dokumentacije in CMF dokumentacijo: ``bash install.sh``;
* Poženite ``make html`` in si oglejte generirani HTML v ``build`` direktoriju.

.. _reStructuredText:        http://docutils.sourceforge.net/rst.html
.. _Sphinx:                  http://sphinx-doc.org/
.. _dokumentov:              https://github.com/symfony/symfony-docs
.. _reStructuredText Primer: http://sphinx-doc.org/rest.html
.. _označevanja:             http://sphinx-doc.org/markup/
.. _Pygments spletni strani: http://pygments.org/languages/
.. _Sphinx hitro nastavitev: http://sphinx-doc.org/tutorial.html#setting-up-the-documentation-sources
