Contribute
==========

This page is intended for developers of (or contributing to) Pypubsub.

.. contents:: In this section:
   :depth: 1
   :local:


.. _label-contributing:

Contributing
------------

Contributions are welcome! There are many ways you could contribute:

- bug fixes
- new features
- test results on different platforms
- documentation
- screencasts! (of applications using Pypubsub with output when user clicks)
- example topic trees (using ``pubsub.utils.printTopicTree()`` in latest
  version, or ``print Publisher`` in versions 1)
- other improvements
- money!

Please contact by posting on the forum pypubsub-dev forum (link in the
:ref:`label-support` section) or via http://github/schollii/pypubsub.


System Requirements
-------------------

In addition to the :ref:`label-install-reqs`, the following are required:

- To run unit tests:

  - pytest

- To generate the docs:

  - sphinx >= 1.4.8
  - In Pypubsub 3.3, which used an older version of sphinx, sphinx had to be patched as per post on
    sphinx-dev, but this no longer seems to be the required:

    .. literalinclude:: sphinx_patch1.txt
    .. literalinclude:: sphinx_patch2.txt

- To change code: PyCharm is recommended (Community Edition is sufficient). Various
  build configurations are available via the Pypubsub project when loaded into PyCharm.


Scripts Available
-----------------

*Unit Testing*:
    The test suite is most conveniently run from PyCharm via the "py.test in suite"
    build configuration. The tests can also be run automatically via pytest suite from
    the :file:`tests` folder.

    Once this passes using the project's default interpreter, a Terminal can be
    opened in PyCharm (or alternately a command shell from Windows), and from
    the Pypubsub root folder, run :command:`tox`. This will
    attempt to run the test suite on Python 3.3, 3.4 and 3.5.

    After changes are committed to github, the Travis CI will automatically
    run the tests on a Linux platform, for all versions of Python supported
    by Pypubsub. The results will be at https://travis-ci.org/schollii/pypubsub/builds.

    There is also a buildbot maintained by Jerome Laheurte to test on additional
    \*nix flavors, including OSX. Test results can be viewed at
    https://jeromelaheurte.net/buildbot/pubsub/console.

*Performance Test*:
    A small performance test is available in the :file:`tests` folder.
    It can be run from PyCharm via the perf build configuration. This will
    generate a new :file:`.pstats` file which can be analysed.
    The test can also be run directly from command shell via
    :command:`python perf.py 1000`.

*Documentation*:
    The documentation can be generated locally on Windows via the Gen Docs build
    configuration in PyCharm. Alternatively, it can be generated by running
    :command:`make html` from the :file:`docs` folder of source
    distribution.

    The documentation is automatically built and available online at
    http://pypubsub.readthedocs.io. The latest from master branch is at
    http://pypubsub.readthedocs.io/en/master/. The stable (released)
    documentation is at http://pypubsub.readthedocs.io/en/stable/.


Releases
--------

Pypubsub uses the latest stable Python packaging and distribution tools:
wheel, twine, and pypi.

Creating a new release involves the following sequence of steps:

- Update src/pubsub/__init__.py for new version # (setup.py uses it)
- Update src/pubsub/RELEASE_NOTES.txt: high-level summary of changes, handling incompatibilities, etc
- In docs folder

  - Update index.rst and docs/installation.rst
  - Update docs/changelog.txt: list of specific changes
  - Regenerate HTML docs, confirm ok (no warnings etc)

- Confirm that pytest suite and tox pass
- Confirm that examples all work (one of the examples requires wxpython)
- Commit to remote master repository
- Confirm that travis CI all pass
- Generate the source and wheel distributions and upload to PyPI (from command line:
  :command:`release.bat`)
- Verify new release info and links on pypi.python.org
- Create new branch (tag) in remote master repository
- Confirm installation will work: attempt to install locally via PyPI, then import
  from Python shell


Py2Exe and cx_Freeze
--------------------

For packaging py2exe or cx_Freeze, see (possibly out of date):

.. toctree::

   py2exe.rst
