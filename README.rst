====================
helm-chart
====================

Project Outline
----------------

Project Goals
'''''''''''''

Make it simple to produce the necessary boilerplate for Kubernetes helm charts

Similar Work
''''''''''''

None


Justification
'''''''''''''

The helm specification is heavily structured and reasonably verbose by nature. It lends itself well to generation


Summary
'''''''

============= ==============
License       Language
------------- --------------
MIT           en-AU [lang]_
============= ==============

Installation
-------------

.. Code:: bash

  $ boilr template download littlemanco/boilr-helm-chart helm-chart
  
Updates
-------

I update these templates regularly. If you need to fetch the newer version, try this:

.. Code:: bash

  $ boilr template download littlemanco/boilr-helm-chart helm-chart -f 

Usage
-----

Swap `foo` and `bar` for your own values.

.. Code:: bash

  $ mkdir foo
  $ cd foo
  $ git init
  $ git remote set-url origin git@github.com:foo/bar.git
  $ boilr template use helm-chart .
  $ git add .
  $ git commit -m "Initial Commit"
  $ git push

Thanks
------

- The team behind boilr (https://github.com/tmrts/boilr)

Contributing
------------

Contributions are always welcome! Nothing is to small, and the best place to start is to open an issue.

References
-----------

.. [lang] Lingoes.net,. (2015). Language Code Table. Retrieved 4 June 2015, from http://www.lingoes.net/en/translator/langcode.htm
