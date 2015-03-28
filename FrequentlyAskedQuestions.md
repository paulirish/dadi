

## DeprecationWarning: NumpyTest ##
If you have NumPy version 1.2.0 or higher installed along with SciPy 0.6.0, you may get many warning messages like:

> DeprecationWarning: NumpyTest will be removed in the next release; please update your code to use nose or unittest

These are from SciPy's internal tests. Each time we import a new SciPy module, a version of this warning is output. It's annoying but is not a signal of a problem. Hopefully an updated version of SciPy will be released that will make the changes required to avoid this warning. If they are really bothersome, you can follow [these suggestions](http://projects.scipy.org/pipermail/scipy-user/2008-September/018220.html).