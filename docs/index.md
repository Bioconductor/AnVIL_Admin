# _Bioconductor_ / _AnVIL_

## Project Activities

This site summarizes ongoing [_Bioconductor_][] development activities
related to [_AnVIL_][]. **Note**: All resources listed are under
development.

Learn more [about][] _Bioconductor_ and _AnVIL_.


## Project Activities Overview

- [Available Now](#now)
- [In Progress](#inprogress)
- [Future](#future)
- [Details](#details)

<a name="now"></a>
### Available Now

- Jupyter-based R / Bioconductor container. Available in the AnVIL and
  [us.gcr.io/broad-dsp-gcr-public/terra-jupyter-bioconductor:0.0.12][].


<a name="inprogress"></a>
### In Progress

- RStudio-based R / Bioconductor docker container. Available at
  [us.gcr.io/anvil-gcr-public/anvil-rstudio-bioconductor:0.0.3][]
- [AnVIL][AnVIL_package] package to provide both developer-oriented
  and user-oriented AnVIL-specific functionality.
- AnVIL / _Bioconductor_ oriented workshops
  - [BCC 2020][]. See R / Bioconductor in the Cloud description [here][]
  - [Bioc 2020][]. Tentative [workshop materials][]
- Continued development of [Training Materials][]
- User tool for instrumentation analysis. Cost estimation of RAM, disk, time,
  etc.


<a name="future"></a>
### Future

- _Kubernetes_ support for _Bioconductor_ in AnVIL

<a name="details"></a>
## Project Activities --  Detailed

This section will provide a more detailed description of projects.

- [Containers](#containers)
- [Developer / User Tools](#tools)

<a name="containers"></a>
### Containers

- Jupyter notebook / _Bioconductor_

  - The latest terra-jupyter-bioconductor docker containers are
    available at [AnVIL][] and on the [Google Container
    Registry][gcr]. These containers have the Bioconductor release
    version 3.10, and R version 3.6 as jupyter notebooks. They work
    like the [bioconductor_docker][] images, with the capability to
    install 'all of' the _Bioconductor_ packages.  This image has been
    tested on Leonardo and installs all but a few packages in
    _Bioconductor_ release 3.10, which fail due to achived CRAN
    dependencies. The github link for this work is [terra-docker][];
    use issues on the [Bioconductor fork][bioconductor-terra-docker]
    for _R_ / _Bioconductor_ content.
  
  - The latest image is [us.gcr.io/broad-dsp-gcr-public/terra-jupyter-bioconductor:0.0.12][].
 
  - Links: [Jupyter github repo][] and [Jupyter Dockerfile][].

- RStudio / _Bioconductor_

  - The terra-rstudio-bioconductor docker container is currenly available as a
  custom 'bring your own' image to terra while work on a fully integrated
  RStudio environment is being developed.
  
  - Links: [RStudio Github repo][] and [RStudio Dockerfile][].
  
  - The image is availlable at
    [us.gcr.io/anvil-gcr-public/anvil-rstudio-bioconductor:0.0.3][]. This
    is just the name of the Docker image, which is hosted on the
    [Google Container Registry][].

- _Kubernetes_

  - [Slides](https://docs.google.com/presentation/d/1Y7g_6X8I6DPaNK84EzWNo1wVpfAwdORGt6kcgcPYOV4/edit?usp=sharing)
  - Illustration of working with R and Kubernetes : https://github.com/shwetagopaul92/hgvarByKub
  - [k8sredis][] An alternative approach: k8s with redis work queue and
  BiocParallel functionality. Start a number of parallel jobs on k8s,
  then an interactive 'manager' (e.g., RStudio session; Jupyter
  notebook).  Once in R one can

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

<a name="tools"></a>
### Developer / User Tools

- [AnVIL package][]

  - This _R_ package currently provides both developer-oriented and
    user-oriented AnVIL-specific functionality.
  - (available) Developer-oriented access to major AnVIL components
    (Terra, Leonardo, Dockstore, and Gen3) REST APIs. Bearer-token
    authentication requires gcloud sdk installation. Work on expanding
    and implemented additional REST APIs in on-going.
  - (available) Developer- and user-oriented facilities for interacting with the
    Google cloud, e.g., `gsutil_*()`, `localize()`, `delocalize()`.
  - (under development) Because the software environment is fixed by
    the container, packages can be pre-built and rapidly installed
    simply by copying from an online repository. We are developing the
    tooling to support this repository (as folders in google buckets)
    and to facilitate easy installation (via the [AnVIL package][]
    `install()` function).


[_Bioconductor_]: https://bioconductor.org
[_AnVIL_]: https://www.genome.gov/27569268/genomic-analysis-visualization-and-informatics-labspace-anvil/
[about]: about
[AnVIL package]: https://github.com/Bioconductor/AnVIL
[Training Materials]: training
[AnVIL]: https://anvil.terra.app
[AnVIL_package]: https://github.com/Bioconductor/AnVIL
[gcr]: https://console.cloud.google.com/gcr/images/broad-dsp-gcr-public/US/terra-jupyter-bioconductor
[bioconductor_docker]: https://github.com/Bioconductor/bioconductor_docker
[terra-docker]: https://github.com/DataBiosphere/terra-docker/tree/master/terra-jupyter-bioconductor
[bioconductor-terra-docker]: https://github.com/Bioconductor/terra-docker
[k8sredis]: https://github.com/Bioconductor/k8sredis
[BCC 2020]: https://bcc2020.github.io/
[here]: https://bcc2020.github.io/training/
[Bioc 2020]: http://bioc2020.bioconductor.org/
[workshop materials]: https://github.com/waldronlab/AnVILWorkshop
[Jupyter github repo]: https://github.com/DataBiosphere/terra-docker/tree/master/terra-jupyter-bioconductor
[Jupyter Dockerfile]: https://github.com/DataBiosphere/terra-docker/blob/master/terra-jupyter-bioconductor/Dockerfile
[us.gcr.io/broad-dsp-gcr-public/terra-jupyter-bioconductor:0.0.12]: https://us.gcr.io/broad-dsp-gcr-public/terra-jupyter-bioconductor:0.0.12
[us.gcr.io/anvil-gcr-public/anvil-rstudio-bioconductor:0.0.3]: https://us.gcr.io/anvil-gcr-public/anvil-rstudio-bioconductor:0.0.3
[RStudio Github repo]: https://github.com/anvilproject/anvil-docker
[RStudio Dockerfile]: https://github.com/anvilproject/anvil-docker/blob/master/anvil-rstudio-bioconductor/Dockerfile
[Google Container Registry]: https://cloud.google.com/container-registry/docs/pushing-and-pulling
