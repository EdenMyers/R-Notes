Minitutorial 1
========================================================

With the aim to provide an example of a complete workflow and to show some useful *techniques* and *functions* when **programming in R** (including how to get the most out of the **documentation**), I have created this *R script*.

I hope someone find it useful.

Using the local help
--------------------
Let's type:
 ---
> The help.search function will open a web page at your default web browser when running this script using **knitr**. This is expected.  
Sometimes though, I received an error:  
**Firefox can't establish a connection to the server at ...**  
I'm still trying to figure out how to keep this from happening.
 
 ---

```r
?help.search;
```

```
## starting httpd help server ... done
```

We see the function **help.search()** can take several *parameters*.  

We will use by now only the arguments *pattern* and *package*.

```r
help.search("remove objects", package = "base")
```

The help page returns:  
 ----
>    **base::rm**      Remove Objects from a Specified Environment  

 ----
If we go to the end of the help page we'll see the following example:  
 ----
>  **rm**(**list** = **ls**())  

 ----  

So, list is one of the arguments of the **rm()** AKA **remove()** function.  

In order to see what the function **ls()** does, type:

```r
?ls();
```


### Run examples:
You can also run the existing examples for a particular function by using the **example()** function.

```r
example(rm)
```

```
## 
## rm> tmp <- 1:4
## 
## rm> ## work with tmp  and cleanup
## rm> rm(tmp)
## 
## rm> ## Not run: 
## rm> ##D ## remove (almost) everything in the working environment.
## rm> ##D ## You will get no warning, so don't do this unless you are really sure.
## rm> ##D rm(list = ls())
## rm> ## End(Not run)
## rm> 
## rm>
```

Vignettes
---------
A "vignette" is a special type of **documentation** that several but not all packages have included.  

When it exists, is the most important source of help for dealing with a particular package.  

You can browse all the vignettes you have at your local R installation the following way:  
### Browse local vignnetes:

```r
browseVignettes(all = T)
```

The **browseVignettes()** function opens your default web browser and displays a list of the available vignettes at your computer and hyperlinks to open them.  

### Review local vignette:
For viewing the vignette for a particular library you can use the **vignette()** function, or via the the **browseVignettes()**:

```r
vignette("Sweave")
```

This will open (usually) a **.pdf** or an **.html** file with the required vignette.

### Review local vignette:

```r
browseVignettes("knitr")
```

The Rdocumentation page
-----------------------
A very nice tool for searching and reading the documentation has been built by the rdocumentation.org.  

From the web page:
 ---
> Rdocumentation is a tool that helps you easily find and browse the documentation of all current and some past packages on CRAN.

 ---

```r
# Uncomment if you want to go to the web page
browseURL("http://www.rdocumentation.org/")
```

### The Rdocumentation package:
There is also a package for using the "rdocumentation" tool inside R.  

It can be found on GitHub.

```r
# Uncomment if you want to go to the web page
browseURL("https://github.com/Data-Camp/Rdocumentation")
```


So let's install it:

### Installing from GitHub:

```r
library(devtools)
```

```
## WARNING: Rtools is required to build R packages, but is not currently installed.
## 
## Please download and install Rtools 3.1 from http://cran.r-project.org/bin/windows/Rtools/ and then run find_rtools().
## 
## Attaching package: 'devtools'
## 
## The following objects are masked from 'package:utils':
## 
##     ?, help
## 
## The following object is masked from 'package:base':
## 
##     system.file
```

```r
install_github("Rdocumentation", "Data-Camp")
```

```
## Installing github repo Rdocumentation/master from Data-Camp
## Downloading master.zip from https://github.com/Data-Camp/Rdocumentation/archive/master.zip
## Installing package from C:\Users\Diego\AppData\Local\Temp\RtmpoT2xvG/master.zip
## Installing Rdocumentation
## "C:/PROGRA~1/R/R-31~1.0/bin/x64/R" --vanilla CMD INSTALL  \
##   "C:\Users\Diego\AppData\Local\Temp\RtmpoT2xvG\devtools864179c63a8\Rdocumentation-master"  \
##   --library="C:/Users/Diego/Documents/R/win-library/3.1" --install-tests
```

### Using the Rdocumentation package

```r
library(Rdocumentation)
```

```
## 
## Attaching package: 'Rdocumentation'
## 
## The following objects are masked from 'package:devtools':
## 
##     ?, help
## 
## The following objects are masked from 'package:utils':
## 
##     ?, help
```

```r
?rm
```

Note Rdocumentation masks the help, so you are redirected to the Rdocumentation web page for reading the help.  

I found it very handy, mostly due the way the help is displayed, because let's face it, the local R documentation is plain, ugly, and difficult to read.

Now that you know this option exists, let's keep using the local help for the rest of this mini-tutorial.

### Unloading a library from a session:

```r
detach("package:Rdocumentation", unload = TRUE)
```

