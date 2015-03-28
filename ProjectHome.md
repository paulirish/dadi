![http://dadi.googlecode.com/svn/wiki/dadi_logo.png](http://dadi.googlecode.com/svn/wiki/dadi_logo.png)
# Diffusion Approximation for Demographic Inference #

∂a∂i implements a method for demographic inference from genetic data, based on a diffusion approximation to the allele frequency spectrum. One of ∂a∂i's main benefits is speed: fitting a two-population model typically takes around 10 minutes, and run time is independent of the number of SNPs in your data set. ∂a∂i is also flexible, handling up to three simultaneous populations, with arbitrary timecourses for population size and migration, plus the possibility of admixture and population-specific selection. The code is young but has already been used in [several publications](PublicationsUsingDadi.md).

Originally ∂a∂i was initially developed by [Ryan Gutenkunst](http://gutengroup.mcb.arizona.edu) in the labs of Scott Williamson and [Carlos Bustamante](http://www.bustamantelab.org) in Cornell's [Department of Biological Statistics and Computational Biology](http://www.bscb.cornell.edu). Ryan is now faculty in [Molecular and Cellular Biology](http://mcb.arizona.edu) at the [University of Arizona](http://www.arizona.edu), and [his group](http://gutengroup.mcb.arizona.edu) continues to work on ∂a∂i.

## News ##
  * **∂a∂i version 1.6.3 released**; Jul 12, 2012
> This release improves optimize\_grid, in response to a request by Xueqiu, and also adds the option to push optimization output to a file. It also includes a fix contributed by Simon Gravel for errors in extrapolation for very large spectra. Finally, spectra calculation for SNPs ascertained by sequencing a single individual has been added, in response to a request by Joe Pickrell.

  * **∂a∂i version 1.6.2 released**; Dec 4, 2011
> This release fixes a long-standing bug in `make_fux_table`. (Testing suggests that in almost all cases the bug had little effect on results.) Also fixed is a bug that prevented optimizations from succeeding.

  * **∂a∂i version 1.6.1 released**; Nov 8, 2011
> This release improves support for modeling admixture. It turns out that when the admixture methods in `PhiManip` are used, this can result in oscillations in the calculated frequency spectrum as the grid size is changes, which invalidates extrapolation. One solution is to run with pts\_l of length one, so there is no extrapolation. Another solution, if the admixture is the last event in your model, is to implement admixture using the new `admix_props` argument to `Spectrum.from_phi`, rather than using the `PhiManip` methods.

## Example ##

![http://dadi.googlecode.com/svn/trunk/examples/YRI_CEU/YRI_CEU.png](http://dadi.googlecode.com/svn/trunk/examples/YRI_CEU/YRI_CEU.png)

The above plot summarizes the result of fitting a model the joint frequency spectrum of genetic variation between the Yoruba (YRI) and CEPH European (CEU) populations. The data is derived from the [Environmental Genome Project SNPs database](http://egp.gs.washington.edu/). The upper left panel is the data, and the upper right is the result of a demographic model whose parameters have been optimized using ∂a∂i. The lower left panel is the residuals between model and data (red means the model predicts too many SNPs in that bin) and the lower right is a histogram of the residuals. The model involves population growth in the ancestral population, followed by divergence of the CEU population with a bottleneck and exponential growth. It contains 7 free parameters and took a few minutes to fit using ∂a∂i.