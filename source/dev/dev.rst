.. _dev-label:

Developer Documentation
=======================

.. note::

  This documentation assumes that you are using a Mac running OS X. Other
  operating systems should work, but we don't have any hanging around to test.

eXistDb & oXygen
----------------

They really do like their silly capitalization don't they?

`eXistDb`_ is a XML database. It's useful for storing documents and
searching or processing them, especially if they don't really fit in a
traditional SQL database. The Wilde Trials and any TEI project will use
eXist as the storage layer. It is open-source and freely available.

`oXygen`_ is an XML editor with built-in schemas for TEI, XHTML, and other document
formats. It also supports XSLT and XQuery transformations via different engines
and validation via RelaxNG, Schematron, and loads of other schemas. It isn't
open-source, nor is it free. But the library has a site license so shouldn't
cost the DHIL anything to use.

Installing eXistDb
------------------

The eXistDb developers distribute their software via `BinTray`_. The page lists
a number of release versions. Navigate to the most recent stable release [#f1]_
and download the ``-setup-VERSION.jar``. This will give you an application that
is easy to configure and run.

Once the .jar file is finished downloading, double click on it and follow the
installation instructions. The application will be installed in
``/Applications/eXist-db`` because developers aren't ever consistent with
naming things.

To run the Wilde Trails application, you must make one change to an eXistDb
configuration file. Open ``/Applications/eXist-db/conf.xml`` in a text editor
and look for this element.

  .. code-block:: xml
    :linenos:
    :lineno-start: 773
    :caption: This line may be in a different position for other versions of eXistDb.

    <xquery enable-java-binding="no" disable-deprecated-functions="no"
            enable-query-rewriting="yes" backwardCompatible="no"
            enforce-index-use="always"
            raise-error-on-failed-retrieval="no">

Change ``enable-java-binding="no"`` to ``enable-java-binding="yes"``, save the
file, and restart eXistDb if you need to.

eXistDb listens on port 8080 by default. If you have installed a web server
it may also be listening on port 8080. Only one program can listen on a port at a time, so
either stop the web server or reconfigure the web server or eXistDb
to listen on another port.

To change eXistDb's port, open ``/Applications/eXist-db/tools/jetty/etc/jetty-http.xml``
and change the port number on line 38. In the examples below, line breaks and
indentation have beeb added to improve readability.

.. code-block:: xml
  :emphasize-lines: 4

  <Set name="port">
    <Property name="jetty.http.port" deprecated="jetty.port">
      <Default>
        <SystemProperty name="jetty.port" default="8080"/>
      </Default>
    </Property>
  </Set>

  If you make this change, you will need to restart eXistDB for it to take
  affect.

Once you have installed and configured eXistDB, you can start the server which
should be installed in your /Applications folder.

Using eXistDb
-------------

The `Dashboard`_ is the starting point to access most of the eXistDB functionality.
The basic install should include these apps, and possibly others. By default
you can login as admin without a password.

Collections
  Browse the data collections stored inside the server

eXide
  An integrated development environment. Useful for making quick edits to files
  stored in the database.

eXist-db Documentation
  An app that contains documentation for the server.

Monex
  A database monitor and profiler, which contains some useful development tools

Package Manager
  Use this tool to install the Wilde Trials Data application.

User Manager
  This tool will let you set passwords and access levels for users in the
  database. You should use it to set a password for the admin user.

XQuery Function Documentation
  Generated API documentation for the libraries and applications installed in
  the server.

Other apps that you have installed to the database using the package manager
will also show up here.

Getting the Wilde Trials App
----------------------------

Once you have eXist up and running, use git to get a copy of the code.

We use `GitHub`_ to manage most of our souce code. Visit the website, sign up,
and we will add you as a contributor to the `SFU DHIL account`_.




Installing & Using oXygen
-------------------------

#. download
#. license
#. install
#. connect to exist
#. create a project

.. rubric:: Footnotes

.. [#f1]

  The preview releases are usually named with a -RC suffix, like 5.0.0-RC1. They
  *should* work fine, but may cause compatibility problems. Stick to the most
  recent, non-preview version.

  .. _eXistDb: http://exist-db.org/exist/apps/homepage/index.html
  .. _oXygen: https://www.oxygenxml.com/
  .. _BinTray: https://bintray.com/existdb/releases/exist


  The Wilde Trials is an `eXistDB`_ app, developed in eXist 4.2. It should be compatible
  with more recent versions of eXist. Find an appropriate version for your OS on
  the eXistDb home page and install it.

.. [#osx]

  The Latest Stable Release is usually the best version. For OS X, download the
  .dmg file and install it as a normal file.

.. _`eXistDB`: http://exist-db.org/exist/apps/homepage/index.html
.. _`Dashboard`: http://localhost:8080/exist/apps/dashboard/index.html
.. _`GitHub`: https://github.com
.. _`SFU DHIL account`: https://github.com/sfu-dhil
