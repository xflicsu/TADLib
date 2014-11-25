Installation Guide for TADLib
==============================

Requirements
============
TADLib is developed and tested on UNIX-like operating system, and following Python
packages are recommended:

- Python (2.x >= 2.6, not compatible with 3.x)
- Numpy (>= 1.6)
- Scipy library (>= 0.10)
- Matplotlib (>= 1.1)
- scikit-learn (>= 0.10)

For *coniss*, additional Python package *rpy2* (a powerful python package
providing simple and robust access to R within python) and two R packages
*rioja* and *vegan* are required.

.. note:: Tested systems: Red Hat Enterprise Linux Server release 6.4 (Santiago),
   CentOS release 6.4 (Final)

Installation
=============
Firstly, install all the required python packages:

There's an exhaustive instruction at http://www.scipy.org/install.html

We strongly recommend using `conda <http://conda.pydata.org/miniconda.html>`_,
an excellent Python package and environment manager.

Once Miniconda is installed, you can use the conda command to install any
other packages. Open a terminal and type::

    $ conda install numpy scipy matplotlib scikit-learn

More details about conda can be found at http://conda.pydata.org/docs/

Then you can install TADLib just as other packages stored in PyPI:

Use *easy_install*::

    $ conda install setuptools
    $ easy_install install TADLib

Or download the `source code <https://pypi.python.org/pypi/TADLib>`_ manually,
extract it and run the setup.py script::

    $ python setup.py install

Finally, run this command in a terminal prompt::

    $ python -m "tadlib.tests.testall"

If no exception occurs, congratulations, TADLib has been installed successfully!

Let's spend a few minutes dealing with *coniss* dependencies:

Download R source code here: http://cran.rstudio.com/, unpack it, change to
the extracted directory, get to a terminal prompt and type::

    $ ./configure --prefix=R_HOME --enable-R-shlib
    $ make
    $ make check
    $ make install

where R_HOME is the installation directory you choose for R.

You may need to reset your PATH and LD_LIBRARY_PATH environment variables
then. Use vi command to add this two lines to ``~``/.bashrc:

- export PATH=R_HOME/bin:$PATH
- export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:R_HOME/lib64/R/lib

To update the environment variables::

    $ source ~/.bashrc

Then it's time to install *rioja* and *vegan*. Open a R prompt::

    > install.packages("rioja")
    > install.packages("vegan")

rpy2 can be installed in this way::

    $ conda install pip python=2.7.5=2
    $ pip install rpy2 singledispatch

To test if rpy2 was installed correctly, run::

    $ python -m "rpy2.tests"
