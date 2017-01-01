==================
Helm Chart Starter
==================

Project Outline
---------------

Project Goals
'''''''''''''

Make it simple to produce the necessary boilerplate for Kubernetes helm charts

Similar Work
''''''''''''

https://github.com/kubernetes/helm/blob/master/pkg/chartutil/create.go

Justification
'''''''''''''

Helm has an existing default chart that it generates. However, more specific guidelines are applied to this chart,
and there is no way to configure the default Helm chart. See:

Summary
'''''''

============= ==============
License       Language
------------- --------------
MIT           en-AU [lang]_
============= ==============

Installation
------------

.. Code:: bash

  $ git clone https://github.com/littlemanco/helm-chart ${HOME}/.helm/starters/littlemanco/chart
  
Updates
-------

I update these templates regularly. If you need to fetch the newer version, cd into the directory and run the git pull.

.. Code:: bash

  $ cd ${HOME}/.helm/starters/littlemanco/chart
  $ git pull

Usage
-----

Helm allows the usage of a "template" chart when creating other charts, as follows:

.. Code:: bash

  $ helm create chart --starter=littlemanco/chart ${CHART_NAME}

Please note: For some reason, helm creates the charts where the files are executable. To fix this, run:

.. Code:: bash

  $ find . -type f  -exec chmod 644 {} \;

This lets us "pre-populate" a chart with much of the boilerplate that is repeated across all projects. Anything that
we know to be unique has a placeholder of the format `__PLACEHOLDER__`, and anything that needs further attention
once the chart has been generated should have a `todo` and extensive documentation.

Not all documentation has been finished (at the time of writing, in fact, none of it does).

Thanks
------

https://github.com/kubernetes/helm


Contributing
------------

Contributions are always welcome! Nothing is to small, and the best place to start is to open an issue.

References
----------

.. [lang] Lingoes.net,. (2015). Language Code Table. Retrieved 4 June 2015, from http://www.lingoes.net/en/translator/langcode.htm
