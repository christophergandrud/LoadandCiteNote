### Notes on Second Submission of Automating R Package Citations in Reproducible Research Documents

#### Comments in response to reviewer concerns

- `LoadandCite` now uses spidering. It only loads packages that aren't already loaded and installs packages/package versions that are not already installed. Users can specify which library to check to see if a package/version is already installed in .libPaths(). A message is also returned informing the user of which packages/versions are already installed. 

- One of the reviewers suggested a work flow that I had not accommodated in the original version: placing `LoadandCite` at the end of a reproducible research document to cite all of the non-base packages that had already been loaded in the current session. I have added this capability. I think, however, that if `LoadandCite` is being used in a `knitr` type document this is probably not the best way to take advantage of the commands capabilities FINISH

- One of the reviewers wondered why `write_bibMini` was used instead of calling `write_bib` directly from `knitr`. There are two reasons for this. The first that this would have made it impossible to install an old version of `knitr`. To make `LoadandCite` easier to use it basically needs to depend on no other packages. The second reason is that `write_bibMini` and `write_bib` are not identical. This is especially true in the newest version. Where the *repmis* version includes citations for R, journal specific formatting, and the ability to output a text file, not just BibTeX. To avoid confusing the two functions I've renamed `write_bibMini`, write_bibExtra. 

- The focus of the command is to cite the R package versions used to create an analysis. As such it does not cite ancillary material, such as journal articles, that do not indicate the versions that were actually used to create an analysis.

- As suggested by both the reviewers, I have expanded the capabilities for installing packages from non-CRAN sources. NEED TO DO.

- It was mentioned that `LoadandCite` only uses the US CRAN mirror. This is incorrect for current package versions. `LoadandCite` always used the CRAN set by the user by default. It also allowed the user to specify a particular mirror with the `repo` argument. Only if the user had not set the mirror at all did it revert to the US mirror. 

- It is true that installing old packages through `LoadandCite` did use the main CRAN archive. The new version now allows uses to choose which archive to install from for both current and old package versions.


- Unit tests are set as dontrun because CRAN doesn't allow packages to be installed in examples. I did create an example that where a package is only loaded and cited. CHECK

