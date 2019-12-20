
###########################
Quattor\::TextRender\::Base
###########################


****
NAME
****


Test::Quattor::TextRender::Base - Base class for unittesting
the templates in ncm-metaconfig and components.

Refer to the specialized Test::Quattor::TextRender::Metaconfig and
Test::Quattor::TextRender::Component for actual usage.

test
====


Run all unittests to validate a set of templates.


mock_textrender
===============


An exported function that mocks ``CAF::TextRender``
to test usage of TT files during regular component use
in unittests. During this phase, ``CAF::TextRender`` has to use
TT files that are being tested, not the ones installed.
(``CAF::TextRender`` has no easy way to do this to
avoid spreading TT files around).

It takes an optional argument ``includepath`` and sets this
as the includepath of ``CAF::TextRender``. The default includepath
is ``target/share/templates/quattor``, where the TT files are
staged during testing via maven (use exported ``$TARGET_TT_DIR``).

To be used as


.. code-block:: perl

     use Test::Quattor::TextRender::Base;
     mock_textrender();


It returns the mock instance. (This is for convenience, you shouldn't
need this (except maybe to ``unmock_all``?). ``Test::MockModule``
keeps a cache of mocked instances, a new call would return the same
instance.)


