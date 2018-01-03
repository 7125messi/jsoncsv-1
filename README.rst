==================
JSON-to-CSV Module
==================

.. image:: https://travis-ci.org/seanfisk/python-project-template.png
   :target: https://travis-ci.org/seanfisk/python-project-template

This script reads JSON-structured data from a file or a URL to extract data and store it into a CSV file.

This program fulfills the following functions:

* Reads JSON data from a file
* Reads JSON data from a URL
* Write JSON data into a CSV file using Unicode


Project Setup
=============

This will be the ``README`` for your project. For now, follow these instructions to get this project template set up correctly. Then, come back and replace the contents of this ``README`` with contents specific to your project.

Python Installation
-------------------

This project requires Python {$version} to run properly. To install the Python interpreter, follow the steps below::

For Windows:
------------

#. Download the latest version of the Python ${version} Windows binary installer at https://www.python.org/downloads/
#. Proceed with the installation by executing the installer program.

For Linux:
----------

#. For Debian/Ubuntu distributions, install the Python interpreter using the following command::

    sudo apt install python

#. To install Python on Fedora/CentOS distributions, use the following::

    yum install python

#. For Arch Linux, simply use the pacman installer::

        pacman -S python

Usage
-----

The script provides the following options from the command-line::

        usage

Instructions
------------

#. Execute the script using the following line::

        python <script>.py -arg1 v -arg2 x

#. Edit the metadata file ``my_module/metadata.py`` to correctly describe your project.

#. Generate files based upon the project metadata you just entered::

        python internal/generate.py

   The generation script will remove all the template files and generate real files, then self-destruct upon completion.

#. Delete the old git history and optionally re-initialize the repository::

        rm -rf .git # or `ri -recurse -force .git' for PowerShell
        git init

#. Change the license in ``setup.py`` and replace the generated ``LICENSE`` file with the one of your choice. If you would like to use the MIT license, no change is necessary.

#. Change the ``classifiers`` keyword in ``setup.py``. This *will* require modification.

#. Replace this ``README`` with your own text.

#. *(Optional, but good practice)* Create a new virtual environment for your project:

   With pyenv_ and pyenv-virtualenv_::

       pyenv virtualenv my-project
       pyenv local my-project

   With virtualenvwrapper_::

       mkvirtualenv my-project

   With plain virtualenv_::

       virtualenv /path/to/my-project-venv
       source /path/to/my-project-venv/bin/activate

   If you are new to virtual environments, please see the `Virtual Environment section`_ of Kenneth Reitz's Python Guide.

#. Install the project's development and runtime requirements::

        pip install -r requirements-dev.txt

#. Install ``argparse`` package when developing for Python 2.6::

        pip install argparse

#. Run the tests::

        paver test_all

   You should see output similar to this::

       $ paver test_all
       ---> pavement.test_all
       No style errors
       ========================================= test session starts =========================================
       platform darwin -- Python 2.7.3 -- pytest-2.3.4
       collected 5 items

       tests/test_main.py .....

       ====================================== 5 passed in 0.05 seconds =======================================
         ___  _   ___ ___ ___ ___
        | _ \/_\ / __/ __| __|   \
        |  _/ _ \\__ \__ \ _|| |) |
        |_|/_/ \_\___/___/___|___/

   The substitution performed is rather naive, so some style errors may be reported if the description or name cause lines to be too long. Correct these manually before moving to the next step. If any unit tests fail to pass, please report an issue.

**Project setup is now complete!**

.. _pyenv: https://github.com/yyuu/pyenv
.. _pyenv-virtualenv: https://github.com/yyuu/pyenv-virtualenv
.. _virtualenvwrapper: http://virtualenvwrapper.readthedocs.org/en/latest/index.html
.. _virtualenv: http://www.virtualenv.org/en/latest/
.. _Virtual Environment section: http://docs.python-guide.org/en/latest/dev/virtualenvs/

Using Paver
-----------

The ``pavement.py`` file comes with a number of tasks already set up for you. You can see a full list by typing ``paver help`` in the project root directory. The following are included::

    Tasks from pavement:
    lint             - Perform PEP8 style check, run PyFlakes, and run McCabe complexity metrics on the code.
    doc_open         - Build the HTML docs and open them in a web browser.
    coverage         - Run tests and show test coverage report.
    doc_watch        - Watch for changes in the Sphinx documentation and rebuild when changed.
    test             - Run the unit tests.
    get_tasks        - Get all paver-defined tasks.
    commit           - Commit only if all the tests pass.
    test_all         - Perform a style check and run all unit tests.

For example, to run the both the unit tests and lint, run the following in the project root directory::

    paver test_all

To build the HTML documentation, then open it in a web browser::

    paver doc_open

Using Tox
---------

Tox is a tool for running your tests on all supported Python versions.
Running it via ``tox`` from the project root directory calls ``paver test_all`` behind the scenes for each Python version,
and does an additional test run to ensure documentation generation works flawlessly.
You can customize the list of supported and thus tested Python versions in the ``tox.ini`` file.

Pip ``requirements[-dev].txt`` files vs. Setuptools ``install_requires`` Keyword
------------------------------------------------------------------

The difference in use case between these two mechanisms can be very confusing. The `pip requirements files`_ is the conventionally-named ``requirements.txt`` that sits in the root directory of many repositories, including this one. The `Setuptools install_requires keyword`_ is the list of dependencies declared in ``setup.py`` that is automatically installed by ``pip`` or ``easy_install`` when a package is installed. They have similar but distinct purposes:

``install_requires`` keyword
    Install runtime dependencies for the package. This list is meant to *exclude* versions of dependent packages that do not work with this Python package. This is intended to be run automatically by ``pip`` or ``easy_install``.

pip requirements file
    Install runtime and/or development dependencies for the package. Replicate an environment by specifying exact versions of packages that are confirmed to work together. The goal is to `ensure repeatability`_ and provide developers with an identical development environment. This is intended to be run manually by the developer using ``pip install -r requirements-dev.txt``.

For more information, see the answer provided by Ian Bicking (author of pip) to `this StackOverflow question`_.

.. _Pip requirements files: http://www.pip-installer.org/en/latest/requirements.html
.. _Setuptools install_requires keyword: http://pythonhosted.org/setuptools/setuptools.html?highlight=install_requires#declaring-dependencies
.. _ensure repeatability: http://www.pip-installer.org/en/latest/cookbook.html#ensuring-repeatability
.. _this StackOverflow question: http://stackoverflow.com/questions/6947988/when-to-use-pip-requirements-file-versus-install-requires-in-setup-py

Supported Python Versions
=========================

Python Project Template supports the following versions out of the box:

* CPython 2.6, 2.7, 3.3
* PyPy 1.9

CPython 3.0-3.2 may also work but are at this point unsupported. PyPy 2.0.2 is known to work but is not run on Travis-CI.

Jython_ and IronPython_ may also work, but have not been tested. If there is interest in support for these alternative implementations, please open a feature request!

.. _Jython: http://jython.org/
.. _IronPython: http://ironpython.net/


Known Issues
============

Please report any bugs or requests that you have using the GitHub issue tracker!

Authors
=======

.. _DeepCode: https://www.deepcode.ca