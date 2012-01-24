This document is meant to be processed with the knitr package, available at CRAN.
knitr is a re-implementation of Sweave which does some nice things with a minimum of code.
For information about the package, see http://yihui.github.com/knitr/ The manuals are 
found under the Demos link - some of them are pretty interesting, but the two main
documents are the Manual and Graphics demos. It's worth downloading both the pdf and .Rnw files 
for reference under each link.

I tried to use figure environments for the code chunks that produce plots, but it created more
problems than it was worth. One alternative, after the document is stabilized, may be to 
define figure numbers as leading comments in the pertinent code chunks so that one can refer
to them that way. It would be nice to have a list of figures in the final document, but the plots 
take up almost as much space as the text and the LaTeX floats get too far away from the text in 
several places. The default behavior in knitr is much more pleasing and lets one get away
with short comments between plot chunks.


Here's how the flow works, more or less:

In R:

library('knitr')
knit('filename.Rnw')

This will process the .Rnw file and output a filename.tex file that can be run with pdflatex.
Very similar to Sweave().

Code chunk headers are currently processed as follows:

** Non-plot code to be processed:

<<name,echo=TRUE>>=
    code
@

** Non-plot code that is not meant to be run but is to be printed in the doc:

<<name,echo=TRUE,eval=FALSE>>=
   code
@


** A single plot:

<<name,fig.width=x,fig.height=y,fig.align=dir,message=FALSE,cache=TRUE>>=
    code 
@

** Multiple plots rendered sequentially, one by one:
<<name,fig.width=x,fig.height=y,message=FALSE,cache=TRUE>>=
    code
@

** Multiple plots rendered side by side (example for two plots):
<<name,fig.width=x,fig.height=y,out.width=.45\textwidth,fig.show=hold,message=FALSE,cache=TRUE>>=
    code
@

where x and y are values in inches (1 in ~ 2.5 cm). These aren't locked in stone - if you
have a better way, feel free to share.

The relevant arguments in the code chunk header are:

fig.width:  actual width of the graphic produced in R
fig.height: actual height -----------  "" ----------
fig.align:  how the figure should be aligned (left,center,right)
out.width:  width of the plot on the printed page
fig.show:   how printed figures should be arranged on a page (asis [default], hold, animate)
               - asis: one plot for each code chunk that produces a plot
               - hold: collates plots until the end, where they are processed as a group
fig.keep:   indicates how plots should be recorded (none, first, last, high [default], all)
               - high: merges low-level plot changes into the previous high-level plot
               - all: keeps low-level changes as separate plots
               - first: keeps only the first plot
               - last: keeps only the last plot
               - all: keeps all plots
message:    should output messages from R be printed in the output?
cache:      should the plots be cached?
dev:        plotting device. knitr supports about 20 graphics devices; I've used two thus
               far: pdf, and png for five graphs whose pdf files exceeded 1Mb each (and choked 
               my printer). The mixture of pdf and png works fine AFAIK. The tikz device 
               is supported if you want to include LaTeX code snippets
               in the graph. See the basic manual for more details.

I haven't done anything fancy - this is my first attempt with knitr, so I've kept it as
basic as possible.

If you have any questions, e-mail me at djmuseR at gmail dot com.

Thanks for contributing!
Dennis