# Frequency spectrum format #

See `help(dadi.Spectrum.to_file)`.

# SNP data format #

Frequency spectra are created from a _data dictionary_ using either the method `Spectrum.from_data_dict` or `Spectrum.from_data_dict_corrected`. For user convenience, the method `Misc.make_data_dict` reads a specific SNP file format to generate an appropriate data dictionary. That SNP file format is described here. An example can be found in the `examples/fs_from_data/data.txt` file included with the ∂a∂i source distribution.

## Details ##

The data file begins with any number of comment lines that being with `#`. The first parsed line is a column header line. No spaces are allowed within any entry in the table. Individual rows make be commented out using `#`.

The first column should contain the ingroup reference sequence at that SNP, including the flanking bases. If the flanking bases are unknown, they can be denoted by `-`. The header label is arbitrary.

The second column should contain the aligned outgroup reference sequence at that SNP, including the flanking bases. Unknown entries can be denoted by `-`. The header label is arbitrary.

The third column gives the first segregating allele. The column header must be **exactly** `Allele1`.

Then follows an arbitrary number of columns, one for each population, each giving the number of times Allele1 was observed in that population. The header for each column should be the population identifier.

The next column gives the second segregating allele. The column header must be **exactly** `Allele2`.

Then follows one column for each population, each giving the number of times Allele2 was observed in that population. The header for each column should be the population identifier, and the columns should be in the same order as for the Allele1 entries.

Then follows an arbitrary number of columns which will be concatenated with `_` to assign a label for each SNP.


## Example ##

The following table gives an example for data from two populations, YRI and CEU.

| Human | Chimp | Allele1 | YRI | CEU | Allele2 | YRI | CEU |  Gene | Position |
|:------|:------|:--------|:----|:----|:--------|:----|:----|:------|:---------|
| ACG       | ATG          | C           | 29     | 24     | T           | 1        | 0       |  abcb1 | 289 |
| CCT       | CCT          | C           | 29     | 23     | G          | 3        | 2       |  abcb1 | 345 |
|... | ... | ... |... |... |... |... |... |... |... |
| ATT     | ATT   |  C |      14 |     10  | T | 15 | 13 | xrcc5 | 101569 |

## Notes ##

The `Allele1` and `Allele2` headers must be exactly those values because the number of columns between those two is used to infer the number of populations in the file.

The method `Spectrum.from_data_dict_corrected` polarizes the SNPs using outgroup information and applies a statistical correction for multiple mutations described in [Hernandez et al. (2007)](http://dx.doi.org/10.1093/molbev/msm108). Any SNPs without full trinucleotide ingroup and outgroup sequences will be ignored, as well as SNPs in which the flanking bases are not conserved between ingroup and outgroup, or in which the outgroup allele is not one of the segregating alleles. The correction uses the expected number of substitutions per site, the trinucleotide mutation rate matrix, and a stationary trinucleotide distribution. These are summarized in a table of misidentification probabilities that can be calculated using `Misc.make_fux_table`. (It should also be possible to develop a correction using only the single-site transition matrix. If this would be helpful, please contact the developers of ∂a∂i.)

The method `Spectrum.from_data_dict` can work with or without outgroup information. If the method parameter `polarized` is `True`, SNPs are ignored for which the outgroup allele is missing, not one of the two segregating alleles, or is `-`. If the method parameter `polarized` is `False`, any outgroup information is ignored, and the returned `Spectrum` is folded.

Note that the total number of calls to `Allele1` and `Allele2` in a given population may not be the same for each SNP. When constructing the `Spectrum` each SNP will be projected down to the requested number of samples in each population. (Note that SNPs cannot be projected up, so SNPs without enough calls in any population will be ignored.)