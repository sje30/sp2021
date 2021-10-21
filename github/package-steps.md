# Making a package cribsheet

We will use devtools for this.

There is an excellent cheat sheet for making packages:
https://github.com/rstudio/cheatsheets/raw/master/package-development.pdf

Check out the others at: https://www.rstudio.com/resources/cheatsheets/


    require(devtools)
    create('~/darts')

Now add some R code to the R folder

    setwd("~/darts")

# add some code

load_all() should now work; best to restart R if you had functions
also in global namespace.


# add some tests

in tests/testthat

# check that DESCRIPTION file.

## use_mit_license()

this will ensure that you use the MIT licence and edits the
description file.


# Document to create help files in man

Add roxygen comments to your R files.

    devtools::document()

this will update NAMESPACE;  don't forget the @export commands.

# data/inst/extdata


# Vignette add a vignette

    use_vignette('estimating')

opens my editor

edit it, then:

    build_vignettes()

# Refine

    check()
	
to fix probems in the package.


# install locally

    install(build_vignettes=TRUE)

# check package works locally

    require(darts)
    vignette('estimating')

# upload it to github

- create 'darts' repo on github

This is the default text to add a readme.
  
    echo "# darts" >> README.md
    git init
    git add README.md
    git commit -m "first commit"
    git branch -M main
    git remote add origin git@github.com:sje30/darts.git
    git push -u origin main



Now we want to add our R code etc; might as well add everything here

    git add .
    git commit -m 'add package code'
    git push


## Installing, checking, and uninstalling

    devtools::install_github('sje30/darts', build_vignettes=TRUE)
    system.file(package='darts')
    require(darts)
    vignette('estimating')
    remove.packages('darts')




