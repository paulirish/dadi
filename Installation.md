# Dependencies #
  * [Python](http://www.python.org/download/) (>= 2.4)
  * [NumPy](http://scipy.org/Download) (>= 1.2.0)
  * [SciPy](http://scipy.org/Download) (>= 0.6.0)
> ### Recommended ###
  * [matplotlib](http://matplotlib.sourceforge.net/) (>= 0.98.1) (used for plotting routines)
  * [IPython](http://ipython.scipy.org/) (much improved python shell)

# Using a released version #

## Linux ##
  1. Unpack the source code tarball `tar xzf dadi-<version>.tar.gz`
  1. In the `dadi-<version>` directory, run `python setup.py install`. This will compile the C modules ∂a∂i uses and install those plus all ∂a∂i Python files in your Python installation's `site-packages` directory.
  1. A (growing) series of tests can be run in the `tests` directory, via `python run_tests.py`

## OS/X and Windows ##
  * The easiest way is to download and run one of the binary installers. Note that we still suggest downloading the source distribution to have access to tests, examples, and documentation.
  * The installation of Python that ships with OS X may not be detected by the binary installer. Please install one of the python.org distributions.
  * Note that installers are specific to the minor version of Python. For example, a 2.5 installer will work on 2.5.1 and 2.5.4, but not on 2.6. If you need a binary installer for a particular version of Python, please ask on the dadi-users mailing list.
  * If you have gcc installed, you can follow the above Linux directions.

# Using the (bleeding-edge) subversion repository version #
  * To get the absolute latest version of ∂a∂i, use the [SVN repository](http://code.google.com/p/dadi/source/checkout).
  * To run from the source directory, use `python setup.py build_ext --inplace.` . This will compile the C modules and leave them in the source tree. Then set your `PYTHONPATH` to include the directory which `setup.py` is in, so that you'll be able to import ∂a∂i.

# General notes #
  * If you follow the instructions here, you should be able to `import dadi` working from any directory on your system, with one exception. You **do not** want to `import dadi` from the `dadi-<version>` directory. This will search down through the source directory for the C modules and will fail when it doesn't find them.

# Mailing lists #
Please sign up for the [dadi-announce](http://groups.google.com/group/dadi-announce) and [dadi-user](http://groups.google.com/group/dadi-user) mailing lists, so we can keep you updated when new versions are released.