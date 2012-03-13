





# Overview

Version 0.9.0 of the **ggplot2** package contains a number of
changes that provide a user with more
flexibility and greater ease of use in the construction of a
ggplot. The two most evident improvements from a user's
perspective are: (i) the help
pages have been expanded considerably, with many new examples; and
(ii) the computing time has been reduced significantly. Several new
geoms are introduced, as well as a few new `stat_`
functions. These will be described in the sections to follow.

## Legend and colorbar guides

Control over legends is greatly expanded in version 0.9.0. Two functions are
discussed in this section: `guide_legend` and
`guide_colorbar`. We discuss these first because they will be
used extensively in the sections to follow.

In the grammar of graphics, there are two types of guides: scale
guides and annotation guides. In the former group lie positional guides
and legends. Annotation guides include `geom_text`, `annotate`
and the new annotation functions.

Each guide function has a number of arguments. The following table lists
those that are common to both legend guides and colorbar guides:

Category   Argument   Notes
title	   title      legend title
	   title.position    `left`, `right`, `top`, `bottom`
	   title.theme	     uses theme_text
	   title.hjust	     horizontal justification
	   title.vjust	     vertical justification
label	   label	     TRUE means labels are drawn
	   label.position    `left`, `right`, `top`, `bottom`
	   label.theme	     uses theme_text
	   label.hjust	     horizontal justification
	   label.vjust	     vertical justification
key options		     default.unit	measurement unit
    direction		     `horizontal` or `vertical`
    reverse		     reverse direction of keys


## guide_legend

This function provides a user with several options to control
features of a legend guide, including titles, labels,
the height and width of legend keys, the direction of the legend and several
other options that are useful when a large number of
categories exist.

The code below creates four rows of legend keys, increases the
font size of the legend title and emboldens it:
![plot of chunk guide-legend-ex1](http://i.imgur.com/kOMam.png) 


The following example concerns an application that comes up occasionally
on the ggplot2 list: overriding the alpha transparency value in
the legend so that the values of an aesthetic are visible in the legend key.
The relevant argument is `override.aes`: in the left side plot, the
very low alpha value makes it impossible to see the legend key items, but
`override.aes` resets the alpha value in the legend to make them
visible in the right hand plot.
![plot of chunk guide-legend-ex3](http://i.imgur.com/CeDJn.png) ![plot of chunk guide-legend-ex3](http://i.imgur.com/oOemR.png) 


