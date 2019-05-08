# Bioconductor / AnVIL 

## Project Activities

This site summarizes ongoing [_Bioconductor_][] development activities
related to [_AnVIL_][]. **Note**: All resources on this page are under
development.

Learn more [about][] _Bioconductor_ and _AnVIL_.

[_Bioconductor_]: https://bioconductor.org
[_AnVIL_]: https://www.genome.gov/27569268/genomic-analysis-visualization-and-informatics-labspace-anvil/
[about]: /about

## Current activities

[AnVIL package][]

- This _R_ package currently provides both developer-oriented and
  user-oriented AnVIL-specific functionality.
  
- (available) Developer-oriented access to major AnVIL components (Terra,
  Leonardo, Dockstore, and Gen3) REST APIs.
  
- (under development) Developer- and user-oriented facilities for
  interacting with the Google cloud, e.g., `localize()`,
  `delocalize()`, `sync()`.
  
- (under development) User-oriented facilities for package
  installation from precompiled binaries.

[AnVIL package]: https://github.com/Bioconductor/AnVIL

[_Bioconductor_ containers][]

- (available) These Docker containers provide the system dependencies (e.g.,
  software libraries) to install 'all of' _Bioconductor_. The
  containers can be used locally or deployed in the _AnVIL_ /
  _Leonardo_ application. 
  
- (under development) Because the software environment is fixed by the
  container, packages can be pre-built and rapidly installed simply by
  copying from an online repository. We are developing the tooling to
  support this repository (as folders in google buckets) and to
  facilitate easy installation (via the [AnVIL package][] `install()`
  function).

[_Bioconductor_ containers]: https://github.com/Bioconductor/AnVIL_Docker

_Illustrative notebooks_

- (available)
    - [Using Bioconductor's VCF processing stack](https://github.com/vjcitn/terravar/blob/master/Tiny%20population%20stratification%20display.ipynb) to demonstrate population stratification using a small slice of chr17 from the [new EBI 1000 genomes VCF](http://ftp.1000genomes.ebi.ac.uk/vol1/ftp/data_collections/1000_genomes_project/release/20190312_biallelic_SNV_and_INDEL/20190312_biallelic_SNV_and_INDEL_README.txt)

_Shiny Apps_

- (available)
    - [TerraPlane](https://github.com/shwetagopaul92/TerraPlane): To help filter dockstore to find methods based on search term
    
_Kubernetes_

- [Slides](https://docs.google.com/presentation/d/1Y7g_6X8I6DPaNK84EzWNo1wVpfAwdORGt6kcgcPYOV4/edit?usp=sharing)
- Illustration of working with R and Kubernetes : https://github.com/shwetagopaul92/hgvarByKub
- [k8s-redis-bioc-example][] An alternative approach: k8s with redis
  work queue and BiocParallel functionality. Start a number of
  parallel jobs on k8s, then an interactive 'manager' (e.g., RStudio
  session; Jupyter notebook).  Once in R one can

    ```
    library(RedisParam)
    fun = function(i, ...) {
        Sys.sleep(1)
        system("hostname", intern=TRUE)
    }
    
    p <- RedisParam(
        workers = 5, jobname = "demo", 
        is.worker = FALSE
    )
    res <- bplapply(1:13, fun, BPPARAM = p)
    
    table(unlist(res))
    ## five-worker-5ns79 five-worker-8gh5q 
    ##                 2                 2
    ## five-worker-dvdtv five-worker-wt5jq
    ##                 3                 3
    ## five-worker-zwlpw
    ##                 3
    ```

[k8s-redis-bioc-example]: https://github.com/mtmorgan/k8s-redis-bioc-example
