```
                         GDSII to svg utility
                        Provided by ecelab.org
                Copyright © 2019. All rights reserved.

Version 1.0.0

```
Intro:
------
```
This utility enables plotting of any module/cell included in a GDSII file to
Scalable Vector Graphics. The output is an .svg file which can be opened with
any browser or other svg viewer applications.

A GDSII file is a database file format and the de facto industry standard for
data exchange of integrated circuit layouts.

Most GDSII viewer applications need a commercial license to be able to use
them. This makes the direct use of GDSII files a cumbersome process. Moreover,
all current viewers can only export GDSII modules as raster image files (e.g. 
.jpg, .png, .bmp), resulting in limited printing and visualization properties.
Instead, a teacher/presenter/instructor can use an svg representation of the
circuit and have unlimited "zoom" to study/examine the layout. Researchers can
embed svg layout images to their research paper, greatly increasing its visual
properties and appeal.
```

Download:
---------
```
The tool is currently offered as binary executable for Unix/Linux and
Microsoft Windows systems.

Unix/Linux download: https://ecelab.org/gds2svg_linux
    Requires GLIBC (libc.so.6) version 2.25 or higher. Tested on Ubuntu 18.04.

Windows 7/8/10 32/64bit download: https://ecelab.org/gds2svg_win
```

Usage:
------
```
This is a command line tool. Unzip the bundled file to your target directory
and run the executable. The filename of the executable is "gds2svg" for the
*nix version and "gds2svg.exe" for the Windows version.

The layer mapping and target coloring configuration are defined in a separate
file, named "layers.cfg". An example of the layer mapping and default colors
for STMicroelectronics 28-nm FD-SOI process is included in the bundle. This
file can be used as a template. Documentation about its format is included
in the header of the file.

Note: current version of the tool does not support datatypes. GDSII files use
a layer number and a datatype to associate each polygon with. This is commonly
shown as a decimal number in the form <layer number>.<datatype>, e.g. "7.0".
Datatypes denote different properties of polygons within the same layer.
For example a datatype "0" usually defines a "drawing" polygon, while a
datatype "32" can define a "pin" polygon. This version of the tool just
ignores datatypes which is equivalent to merging all datatypes and assigning
them the same properties as the layer number, as defined in the "layers.cfg"
file. Future releases of the tool will support datatypes.


Usage: "gds2svg <GDSII filename> [optional arguments]"
_______________________

Optional arguments:
<cell name(s)>:         Define the cell, or cells, to be plotted; multiple cell
                        names are separated by one or more spaces; if omitted,
                        the tool plots the top level cell (or all top level
                        cells if there are multiple) found in the GDSII file.
--flat:                 Generates a flat svg file; all cells are flattened out
                        and the svg contains only polygons, i.e. no hierarchy/
                        instantiations; note: svg file can get very large with
                        complex hierarchical designs.
--margin=<val>:         Sets the margin between the outer design coordinates
                        and the final svg size; can be set either as percentage
                        (with a trailing "%") or as absolute number; if given
                        as percentage, the margin is calculated from the
                        largest side of the cell; if given as absolute number,
                        it denotes length units in the same magnitude as the
                        GDSII file (e.g. nm); can be integer or decimal; if
                        omitted, the margin will be set at 2% by default.
--max_width=<val>:      Sets the maximum svg width in pixels; the tool will
                        automatically resize the design to fit set value; it
                        works in conjuction with the "max_height" setting: the
                        design will be scaled by such factor so that its largest
                        side will fit to the smallest of "max_width",
                        "max_height"; should be integer; if omitted, is set to
                        1920 by default.
--max_height=<val>:     Sets the maximum svg height in pixels; the tool will
                        automatically resize the design to fit set value; it
                        works in conjuction with the "max_width" setting: the
                        design will be scaled by such factor so that its largest
                        side will fit to the smallest of "max_width",
                        "max_height"; should be integer; if omitted, is set to
                        4000 by default.
--pdf:                  Generates a pdf, in addition to svg file; requires
                        "inkscape" installed.
-h or --help:           This screen.
_______________________
```
