This document is meant to be processed with the knitr package, a re-implementation 
and generalization of Sweave that takes the concept of report generation with code to
an entirely different level. For information about the package, see http://yihui.name/knitr/ 
Look under the Demos link for a growing body of documentation. 

The structure of code chunks in knitr is similar to that of Sweave, but the arguments in
the header are, in general, different. The basic structure is

```r
<<name,arg1=val1,arg2=val2,...,argk=valk>>=
    your code here
@
```
where the first argument is the name of the chunk and the remaining arguments are chunk options.
See http://yihui.name/knitr/options for further details.

The source file ggplot2-0.9.0.Rnw is contained in this repo.
To run the source code yourself in R, you need the latest version of knitr and a 
version of ggplot2 that is at least 0.9.0 (at the time this is [re]written, the current version 
is 0.9.3).

After downloading the source file, put it into a directory. By default, it will create a color 
version. From the command line prompt, typing

```r
library('knitr')
knit2pdf('ggplot2-0.9.0.Rnw')
```

will process the .Rnw file and output both a ggplot2-0.9.0.tex file and a corresponding pdf file. 

To get a B/W copy, for example to print on a B/W printer, create a subdirectory named bw in
the directory that contains the .Rnw file. Start up R and setwd() to the directory containing 
the .Rnw file. From the directory containing the .Rnw file, type the following from the command
line:

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
