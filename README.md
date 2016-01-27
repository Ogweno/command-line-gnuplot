### NAME
**gplot** - a command line plotting tool for text data files.

### AUTHOR

Saurabh Paul

### SYNOPSIS
**gplot** [ options ] [ filename ]

### DESCRIPTION
**gplot**  is a command-line plotting tool which uses gnuplot for plotting text data files of the type X,Y1,Y2,...Yn. The data has to be in the form of separate columns,  and  not comma separated. Any comment line has to begin with `#`. It only plots the first nine Y columns for data files with columns `n > 9` with different lines. It is not for scatter  plots. The output plot is a PDF file.  **gplot** uses evince to display the PDF file. The default option is designed for quick plotting so as to get a feel for the  data  file, and as such, the output PDF file is automatically deleted after exiting the command. If it is desired to save the file,  use  the  -save  option instead.

### OPTIONS
`-save filename`

Auto  saves  the output pdf file after exit. For data file filename.*, it saves the PDF file as filename.pdf. It uses the option -range and prompts for  plot  range.  In  addition,  it provides the option to smooth y data  using either csplines or bezier, enter axes labels (in  gnuplot  format), individual  plot  titles  (in  gnuplot format) and the option to move the legend to the top left (tl), top right (tr), left bottom (lb)  and  right bottom  (rb) positions. The user can skip all these options by pressing ENTER after every prompt, in which case default options will be used.

`-range filename`

Provide plot range in the format `[xmin:xmax]` `[ymin:ymax]`, including the square braces. Using  `[:]` for `[xmin:xmax]` will autoscale the x-axis and similar for y-axis. Thus, a combination of `[:]` and numeric entries may be used to  selectively  autoscale or manually scale one or the other axis. Simply pressing ENTER without entering any plot range or a wrong  entry will automatically assume autoscale for both axes. Note, -range option is intended for quick plot range changes, and it does not allow to save  the output file and cannot be used along with -save option. If it is desired to save the output PDF, use -save option, which automatically  allows  to manually enter the plot range.

`-absy -range|-save`

Plots abs(y) vs x.

`-absx -range|-save`

Plots y vs abs(x).

`-absxy -range|-save`

Plots abs(y) vs abs(x)

`-logy -range|-save`

Plots abs(y) vs x with logarithmic scaling for y-axis.

 `-logx -range|-save`

Plots y vs abs(x) with logarithmic scaling for x-axis.

`-logxy -range|-save`

Plots abs(y) vs abs(x) with logarithmic scaling for both x and y axes.


`-expr -range|-save`

Plots  expr(y) vs x, where expr(y) is any mathematical expression involving y data. For example, if the user wants to plot the square of  y  data values vs x, at the command prompt, enter y**2. This mathematical expression will be applied to all y data  columns.  All  standard  mathematical expressions available in gnuplot can be used.

`-exprlogy -range|-save`

Plots absolute value of expr(y) vs x with logarithmic scaling for y-axis.

`-exprlogx -range|-save`

Plots expr(y) vs abs(x) with logarithmic scaling for x-axis.

`-exprlogxy -range|-save`

Plots  absolute  value  of expr(y) vs abs(x) with logarithmic scaling for both x and y axes.



### FILES
**gplot** looks for files in the working directory. Files with absolute or relative pathnames  are not admitted so far. If no filename or a non-existing filename is provided, **gplot** prompts an error message. A typical data file should have the following format:

```
# comment 1
# comment 2
# comment 3
#  X     Y0     Y1    Y2
   1.0   1.2   3.2   4.3
   2.0   1.8   2.3   5.4
   3.0   1.6   4.2   4.4
```

If by  mistake, a  file  not  in  the  `X, Y0, Y1,...` format is used and the file exists, `evince` prompts an error message. The file can also contain comment lines starting with `#`, which is a standard gnuplot feature.

### Installation

The `gplot` command utility can be downloaded and moved to `/usr/local/bin` using `sudo mv gplot /usr/local/bin`. There is also a man file for gplot, the file named `gplot.1`. This can be moved to `/usr/local/man/man1/` in ubuntu to make it available as a man page, and can be accessed using `man gplot`.
