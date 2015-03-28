# Old News #
  * **∂a∂i version 1.6 released**; July 8, 2011
> This release introduces support for modeling temporal samples, in which samples from different timepoints are compared. This is implemented through `freeze` arguments to the `Integration` functions. See the manual under "Ancient Sequences" for more information.

  * **∂a∂i version 1.5.3 released**; May 25, 2011
> This release includes numerous small bug fixes and enhancements. Also, binaries are now provided for Python 2.7.

  * **∂a∂i version 1.5.2 released**; October 6, 2010
> This release reverts to the previously used optimizer, as the bounded version can be much slower if the maximum-likelihood parameters are far from the parameter bounds.

  * **∂a∂i version 1.5.1 released**; August 6, 2010
> The big news for this release is the use of an improved version of the BFGS optimizer, which deals with bounded parameters much better. This should dramatically speed up fits when the optimal parameters are at one or more of the bounds. There are also several minor bugfixes.

> The new optimizer is a scipy wrapper of code developed by Ciyou Zhu, Richard Byrd, and Jorge Nocedal. The algorithm is described in RH Byrd, P Lu, J Nocedal _SIAM J Sci Stat Comput_ 16:1190 (1995) and C Zhu, RH Byrd, J Nocedal _ACM T Math Software_ 23:550 (1997).

  * **∂a∂i version 1.5.0 released**; July 13, 2010
> The first major enhancement in this release is the use of a new default grid for integrating the PDE. The new `Numerics.exponential_grid` was suggested by Simon Gravel. It is more tightly packed toward x=0 and x=1 than the old grid. Additionally, the integration over the PDE result to get the FS has been improved by using a more analytic formulation. As a result, you should get much more accurate results with lower numbers of grid points. Hopefully this will speed up your analyses.

> Additionally, methods were added to `dadi.Plotting` to plot 3D spectra. This includes a method which employs MayaVi2, a remarkable visualization library. If you wish to use this function, you'll need to install MayaVi2, which is most easily accomplished through the Enthought Python Distribution.

  * **∂a∂i version 1.4.1 released**; April 20, 2010
> This release enhances Windows compatibility (thanks to Eduardo Guerra Amorim for testing). An installer for Windows is now provided. Also, a grid parameter search method was added.

  * **∂a∂i version 1.4.0 released**; March 9, 2010
> This release of ∂a∂i includes our first formal manual, plus small changes to improve ease-of-use. The manual is in `doc/manual/manual.pdf` or it can be accessed from the link on the right. An option was added to the optimization methods to hold particular parameters at fixed values, easing likelihood-ratio testing.

  * **∂a∂i version 1.3.4 released**; February 9, 2010
> This release of ∂a∂i includes two small changes to improve ease-of-use. First, population ids are now stored in the Spectrum objects, and these will be used by default in plotting routines. Second, the model-fitting methods have been updated to support models with extra fixed parameters. For example, one might want to analyze different data sets with different fixed values of theta, and this will help support that usage.

  * **∂a∂i paper published**; November 6, 2009
> PLoS Genetics has published [the paper describing ∂a∂i](http://dx.doi.org/10.1371/journal.pgen.1000695).

> Also, I have posted source code for ∂a∂i 1.3.3. This release fixes a minor bug (which did not affect computation results), and hopefully enables Python 2.4 compatibility.

> The paper describes the method and infers demographic models for human expansion out of Africa and the settlement of the New World. The out of Africa model is then combined with a previously estimated distribution of selection coefficients to accurately predict the distribution of segregating nonsynonymous variation between populations.

  * **∂a∂i version 1.3.0 released**; October 22, 2009
> This release of ∂a∂i includes two substantial changes to improve ease-of-use. In addition, the tests suite has been expanded.
    * The `Misc.make_data_dict` function has been added to ease import of data into ∂a∂i. See DataFormats for details on the file format for this method.
    * `Spectrum` objects now track whether or not they are folded. This reduces the potential for mistakes, and it allows operations like projection and marginalization of folded spectra to be handled automatically and correctly.

  * **Paper accepted!**; September 7, 2009
> The paper on ∂a∂i has been accepted for publication in PLoS Genetics. It has also been posted [on the arXiv](http://arxiv.org/abs/0909.0925).

  * **Version 1.2.3 release**; May 21, 2009
> Primarily, this version fixes several small bugs. It also adds an extension of the IM model to Demographics2D, support for pulling specific populations out of an ms file, and a non-log-parameters optimization method.

  * **Version 1.2.2 release**; March 23, 2009
> Added method to import frequency spectra from [SFS\_CODE](http://sfscode.sourceforge.net/) output. Also added the classic Isolation-Migration model to Demographics2D. Finally, some small bugfixes and additional technical features were added.

  * **Version 1.2.1 released**; February 17, 2009
> Added support for Hessian calculation, which can be used to roughly estimate uncertainties.  Additionally, crashing bug related to saving spectra to file was fixed.

  * **Version 1.2.0 released**; January 23, 2009

> The way in which integration timesteps are assigned was changed. The new method better respects the symmetries in the diffusion equation and yields more stable results in extrapolation. This will require changes to user code. See the `YRI_CEU` example for hints as to what is needed.

> Also, support was added for bias correction in the case in which SNPs were ascertained as heterozygous in sequencing one individual (who is not in the current sample). This allows ∂a∂i to be applied to certain genotyping data sets.

  * **Version 1.1.0 released**; November 20, 2008
> Support was added for dominant selection. In addition, `∂a∂i.Misc` now includes a method to generate the table of `f_{ux}` that is needed for applying the ancestral misidentification correction.

  * **Version 1.0.0 released**; November 11, 2008
> To the right (under featured downloads) you will find the source for ∂a∂i-1.0.0 and an installer for Mac OS X. Included in the source distribution are a couple of short examples of using ∂a∂i. Also included is API documentation ∂a∂i's functions (also linked to the right). Enjoy!

  * **Public release soon**; October 16, 2008
> As we've been presenting our results, people have been asking if they can use ∂a∂i on their own data. Rest assured, ∂a∂i will be made freely available in a form that you can use. We're not, however, quite there yet. In particular, useful documentation is forthcoming. We expect to have it up (and ∂a∂i's first official release) by the middle of November. If you subscribe to the dadi-announce mailing list (see link to right), you'll be informed by email when ∂a∂i is officially released and upon major updates.