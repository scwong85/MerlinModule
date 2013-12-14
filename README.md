MerlinModule
==========
In this module, there are two main functions designed specifically to process and parse [Merlin](http://www.sph.umich.edu/csg/abecasis/merlin/tour/linkage.html) data:

* Extract error list from pedstats output
* Mask genotypes from SNPs which produce Mendelian error 


Files
-----
* setup.py
* merlinmod.py
* README.md

Installing merlinmod
--------------------

    python setup.py install


Using the methods in merlinmod.py
---------------------------------
After installation, to use the package in the python code, type:

    from merlinmod import merlinmod
    p = merlinmod()                   #initialise class variable
    p.functionName(argument)          #function call  


Main functions
--------------

    mErrExtract(pedfile, errfile)
Extract Mendelian errors from pedstats output. The format of input file are as below:

> pedfile: linkage pedigree file, TAB delimited, the first six columns represent familyID, sampleID, fatherID, motherID, sex, affection status. The 7th column onwards represent genotype information from each SNP. Each allele will occupied one column.

> The errfile was the output from pedstats:

> pedstats -p pedfile -d datfile > errfile

Output: **error_list.txt**
<dl>
  <dd> Error list generated from mErrExtract function, TAB delimited file with header. First column = sampleID, second column = SNPID </dd>
</dl>
    mMaskErr(pedfile, datfile, error_list)
Mask genotypes which generate Mendelian error. The format of input files are as below:

> pedfile: linkage pedigree file, TAB delimited, the first six columns represent familyID, sampleID, fatherID, motherID, sex, affection status. The 7th column onwards represent genotype information from each SNP. Each allele will occupied one column.

> datfile: linkage dat file, TAB delimited, as described [here] (http://www.sph.umich.edu/csg/abecasis/merlin/tour/input_files.html)

> error_list:
> Error list generated from mErrExtract function, TAB delimited file with header. First column = sampleID, second column = SNPID

Output: **masked_pedfile**
<dl>
  <dd> Pedfile with masked genotype </dd>
</dl>






