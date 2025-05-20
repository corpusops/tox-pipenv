
DISCLAIMER - ABANDONED/UNMAINTAINED CODE / DO NOT USE
=======================================================
While this repository has been inactive for some time, this formal notice, issued on **December 10, 2024**, serves as the official declaration to clarify the situation. Consequently, this repository and all associated resources (including related projects, code, documentation, and distributed packages such as Docker images, PyPI packages, etc.) are now explicitly declared **unmaintained** and **abandoned**.

I would like to remind everyone that this project’s free license has always been based on the principle that the software is provided "AS-IS", without any warranty or expectation of liability or maintenance from the maintainer.
As such, it is used solely at the user's own risk, with no warranty or liability from the maintainer, including but not limited to any damages arising from its use.

Due to the enactment of the Cyber Resilience Act (EU Regulation 2024/2847), which significantly alters the regulatory framework, including penalties of up to €15M, combined with its demands for **unpaid** and **indefinite** liability, it has become untenable for me to continue maintaining all my Open Source Projects as a natural person.
The new regulations impose personal liability risks and create an unacceptable burden, regardless of my personal situation now or in the future, particularly when the work is done voluntarily and without compensation.

**No further technical support, updates (including security patches), or maintenance, of any kind, will be provided.**

These resources may remain online, but solely for public archiving, documentation, and educational purposes.

Users are strongly advised not to use these resources in any active or production-related projects, and to seek alternative solutions that comply with the new legal requirements (EU CRA).

**Using these resources outside of these contexts is strictly prohibited and is done at your own risk.**

This project has been transfered to Makina Corpus <freesoftware@makina-corpus.com> ( https://makina-corpus.com ). This project and its associated resources, including published resources related to this project (e.g., from PyPI, Docker Hub, GitHub, etc.), may be removed starting **March 15, 2025**, especially if the CRA’s risks remain disproportionate.

tox-pipenv
==========

.. image:: https://img.shields.io/pypi/v/tox-pipenv.svg
        :target: https://pypi.python.org/pypi/tox-pipenv

.. image:: https://img.shields.io/travis/tox-dev/tox-pipenv.svg
        :target: https://travis-ci.org/tox-dev/tox-pipenv

.. image:: https://codecov.io/gh/tox-dev/tox-pipenv/branch/master/graph/badge.svg
        :target: https://codecov.io/gh/tox-dev/tox-pipenv

.. image:: https://pyup.io/repos/github/tox-dev/tox-pipenv/shield.svg
     :target: https://pyup.io/repos/github/tox-dev/tox-pipenv/
     :alt: Updates

.. image:: https://pyup.io/repos/github/tox-dev/tox-pipenv/python-3-shield.svg
     :target: https://pyup.io/repos/github/tox-dev/tox-pipenv/
     :alt: Python 3

A tox plugin to replace the default use of virtualenv with Pipenv.

This is a convenient way to retain your use of Pipenv, whilst testing multiple versions of Python.

Installation
------------

.. code-block:: bash

    pip install tox-pipenv

Or, 

.. code-block:: bash

    pipenv install tox-pipenv  

Creating virtual environments
-----------------------------

With this plugin, tox will use `pipenv --python {python binary}` as given to the tox interpreter for each python path.

If you already have virtual environments cached with tox, use the --recreate flag to recreate them with pipenv.

Note: tox will pass the --site-packages flag to pipenv if this is configured in your tox config.

The Pipfile will exist in .tox/{env}/Pipfile as well as Pipfile.lock

Installing requirements
-----------------------

The installation of requirements from your tox config will be passed to pipenv install for installation into the virtual 
environment. This replaces the use of pip within tox.

``requirements.txt`` files will also be parsed by Pipenv and used for each test environment

Executing tests
---------------

Each of the commands in your testenv configuration will be passed to pipenv to execute within the pipenv virtual environment

Example tox.ini
---------------

This simple example will test against Python 2.7 and 3.6 using pytest to execute the tests.

.. code-block:: 

        [tox]
        envlist = py27, py36

        [testenv]
        deps = 
            pytest
            pytest-mock
        commands = python -m pytest test/


Frequently asked questions
--------------------------

Where to install
~~~~~~~~~~~~~~~~

Tox-Pipenv should be installed in the same environment as Tox, whether that is in a virtualenvironment, system environment or user environment. Tox-Pipenv depends on
Tox 3.0 or newer.

Is user expected to create `Pipfile` and `Pipfile.lock` before executing `tox` with this plugin?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes, although if you are migrating from a requirements.txt to a Pipfile, you can use Pipenv to create the Pipfile for you.

Is `Pipfile.lock` expected to be under source control?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

According to `pipenv` documenation, `Pipfile.lock` is not recommended under source control if it is going to be used under multiple Python versions.

What is the role of `requirements.txt` file?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Often, `tox` users use `requirements.txt` which is then referenced from within `tox.ini` file as deps. Pipenv will automatically install any packages listed in 
`requirements.txt` for each virtual environment that Tox creates.

Is `tox.ini` `deps` section really in control?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No, this is a known limitation. 


Authors
-------

* Anthony Shaw
* Omer Katz
* Almog Cohen
