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

To process this document in R, you need the development versions of ggplot2, scales and 
knitr, which in turn means that you need to have Rtools loaded. To install the correct 
versions of the packages,

```r
library('devtools')
dev_mode()    # should reply 'dev_mode ON'
install_github('ggplot2')
install_github('scales', 'hadley')
install_github('knitr', 'yihui')
```

Continuing,

```r
library('ggplot2')
library('scales')
library('knitr')
knit('filename.Rnw')
```

will process the .Rnw file and output a filename.tex file that can be run with pdflatex, either
from the command line or inside an IDE such as Eclipse or Emacs. Very similar to Sweave(). 

To get a color copy of the transition guide, create a subdirectory under the one where the .Rnw 
resides; let's call it col. For B/W, create another directory named bw.

Start up R and setwd() to the directory containing the .Rnw file. Then for color:

```r
setwd('./col')
bw_version <- FALSE
opts_chunk$set(highlight=TRUE)
knit2pdf('../ggplot2-0.9.0.Rnw')
```

For a B/W friendly version: from the directory with the .Rnw file,

```r
setwd('./bw')
bw_version <- TRUE
opts_chunk$set(highlight=FALSE)
knit2pdf('../ggplot2-0.9.0.Rnw')
```

That's it. Thanks to Yihui Xie for the script, and of course, for the knitr package.

If you have any questions, e-mail me at djmuseR at gmail dot com.

Thanks for contributing!
Dennis