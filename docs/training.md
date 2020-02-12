# _Bioconductor_ / _AnVIL_

## Training material

The material here is 'in development' and meant to orient the
_Bioconductor_ community to use of _AnVIL_ resources. See also [AnVIL
documentation][AnVIL-docs] resources.

[AnVIL-docs]: https://support.terra.bio/hc/en-us

- [Workshops](#workshops)
- [_Terra_ workspaces / workflows](#workspaces)
- [Notebooks](#notebooks)
- [Dockstore](#dockstore)
- [Other](#other)

<a name="workshops"></a>
### Workshops

- [Terra in the Classroom][]

  - Documentation on running a small course utilizing AnVIL. This includes some
    set up information as well as the learned positives and negatives as of
    February 2020.


<a name="workspaces"></a>
### _Terra_ Workspaces / Workflows

- (proof-of-principle) A workspace for [pan-cancer transcriptome
  surveys][pancanlink].  This workspace includes two workflows, each
  devoted to different gene sets.  The WDL and associated scripts are
  [registered][dockstorelink] at dockstore.org.  Unit testing for the
  script components is managed in the Bioconductor [BiocOncoTK
  package][vjconcohub] (developer repo).

[pancanlink]: https://app.terra.bio/#workspaces/landmarkanvil2/pancan_tx_public
[dockstorelink]: https://dockstore.org/workflows/github.com/vjcitn/BiocOncoTK/msireg1:master?tab=info
[vjconcohub]: https://github.com/vjcitn/BiocOncoTK/blob/master/tests/testthat/test_dockstore_scripts.R


<a name="notebooks"></a>
### Notebooks

- (proof-of-principle) [Using Bioconductor's VCF processing stack][vcf stack]
  to demonstrate population stratification using a small slice of
  chr17 from the [new EBI 1000 genomes VCF][1kvcf].

- (proof-of-principle) [Using dockstore+terra for pancancer
  transcriptomics][pancantx] to compare relationships between gene
  expression and stratified or continuous measures of microsatellite
  instability in 33 TCGA tumor types.

[vcf stack]: https://nbviewer.jupyter.org/github/vjcitn/terravar/blob/master/Tiny%20population%20stratification%20display.ipynb
[1kvcf]: http://ftp.1000genomes.ebi.ac.uk/vol1/ftp/data_collections/1000_genomes_project/release/20190312_biallelic_SNV_and_INDEL/20190312_biallelic_SNV_and_INDEL_README.txt
[pancantx]: https://nbviewer.jupyter.org/github/vjcitn/terravar/blob/master/trimmedMondaySep16.ipynb

<a name="dockstore"></a>
### Dockstore

<a name="other"></a>
### Other

- Shiny Apps

  - [TerraPlane][] to help filter dockstore to find methods based on search term

- Data management utilies

  - _R_ markdown for [using terra to survey CCDG and
    CMG](training/basicData.Rmd)

	- Results as of 20 June 2019
  ```
  ## # A tibble: 10 x 3
  ## # Groups:   study [2]
  ##    study organ      N
  ##    <chr> <chr>  <int>
  ##  1 CCDG  AI      9031
  ##  2 CCDG  CVD    25741
  ##  3 CCDG  NP     19422
  ##  4 CMG   Blood    277
  ##  5 CMG   Brain   1844
  ##  6 CMG   Eye      552
  ##  7 CMG   Heart    184
  ##  8 CMG   Kidney   432
  ##  9 CMG   Muscle  1722
  ## 10 CMG   Orphan   717
  ```

	- Drilling down on CCDG
  ```
  ## # A tibble: 9 x 4
  ## # Groups:   study, organ [3]
  ##   study organ addit         N
  ##   <chr> <chr> <chr>     <int>
  ## 1 CCDG  AI    Asthma     1171
  ## 2 CCDG  AI    IBD        4694
  ## 3 CCDG  AI    T1D        3166
  ## 4 CCDG  CVD   AFib       3731
  ## 5 CCDG  CVD   EOCAD     20156
  ## 6 CCDG  CVD   HemStroke  1358
  ## 7 CCDG  CVD   Stroke      496
  ## 8 CCDG  NP    Alz        2374
  ## 9 CCDG  NP    Autism    17048
  ```

[TerraPlane]: https://github.com/shwetagopaul92/TerraPlane
[Terra in the Classroom]: https://docs.google.com/presentation/d/1AvEt6UIIx-G5eTe4hlfkGOYsUcSQrKx8ySlnnfg7XH8/edit?usp=sharing