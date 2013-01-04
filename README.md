This document is meant to be processed with the knitr package. knitr is a re-implementation 
of Sweave which does some nice things with a minimum of code.
For information about the package, see http://yihui.name/knitr/ Look under the
Demos link for a growing body of documentation - the two main documents are the Manual 
and Graphics demos. To learn how the package works, it's worth downloading both the pdf 
and .Rnw files under each link.

The structure of code chunks in knitr is similar to that of Sweave, but the arguments in
the header are, in general, different. The basic structure is

```r
<<name,arg1=val1,arg2=val2,...,argk=valk>>=
    your code here
@
```

A color pdf version of this document is included in the repo along with the .Rnw source file.
If you want to run the source code yourself in R, you need the latest version of knitr and a 
version of ggplot2 greater than 0.9.0 (at the time this is (re)written, the current version 
is 0.9.3).

Continuing,

```r
library('knitr')
knit2pdf('ggplot2-0.9.0.Rnw')
```

will process the .Rnw file and output both a ggplot2-0.9.0.tex file that can be run with pdflatex
and a corresponding pdf file. The default version is in color.

To get a B/W copy, for example to print on a B/W printer, create a subdirectory named bw.
Start up R and setwd() to the directory containing the .Rnw file. From the directory 
containing the .Rnw file,

```r
setwd('./bw')
bw_version <- TRUE
knit2pdf('../ggplot2-0.9.0.Rnw')
```

That's it. Thanks to Yihui Xie for fixing up the document to make it compatible with the
current version of the superb knitr package.

If you have any questions, e-mail me at djmuseR at gmail dot com.

Thanks!
Dennis
