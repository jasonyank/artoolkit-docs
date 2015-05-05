# Using 2D Barcode Markers

## About 2D-barcode markers

ARToolKit is well known for the appearance of its markers: square markers with a black border, and with an arbitrary user-definable image in the interior. The Hiro marker used by default by the ARToolKit examples is an iconic example. The pattern inside the marker allows multiple markers to be used to represent different objects or coordinate systems in an AR application. Additionally, the pattern performs an important function in calculating the orientation of the marker, since it distinguishes between the four possible orientations a square marker could hold, i.e. it determines which direction (in the marker plane) the marker is facing.

However, using arbitrary patterns inside a marker comes with some computational cost... the interior of every black square in the image captured from the camera must be compared against every known marker pattern at all four possible orientations. For a handful of markers, this computation comes at small cost, but as the number of markers in use in a single tracker rises to 20 or 100, the cost becomes significant. Additionally, pattern based markers are more likely to be confused by the tracker when there are a large number of markers (since there is a lower degree of uniqueness within the set of markers), leading to markers being misrepresented as each other.

The solution to the tracking difficulties caused by large number of markers is to use so-called 2D barcode markers. These markers no longer have arbitrary user-defined patterns in the interior. Instead, they have a predetermined pattern of black and white squares in a regular matrix. ARToolKit treats the pattern of the squares in the matrix as a two-dimensional barcode, with a unique identification number being associated with each possible pattern of markers.

2D-barcode markers are recognised in constant time, so large numbers of them can be used at little extra computational cost. Additionally, when using 2D-barcode markers, there is a lower probablity of one marker being mistaken for another. The downside is of course that the pattern inside the printed markers is no longer pictorial.

## Using 2D-barcode markers

Support for 2D-barcode markers has been available in all versions of ARToolKit Professional since v4.0, and 2D-barcode markers are now the default format for multi-marker sets, since they offer such radical performance improvements when using multi-marker sets.

The easiest way to use 2D-barcode markers in ARToolKit is to define a multi-marker configuration file for each set, as many files as you wish to track sets. E.g., to use 3 multi-marker sets, two of them on the six faces each of two cubes, and one on a large sheet covering a table-top surface, you would define 3 multi-marker config files.

The default barcode size for 2D-barcode markers in ARToolKit Professional is a 3x3 pattern. A total of 64 possible markers are possible with this arrangement, which is enough for most tabletop AR applications. You will find graphics for the 3x3 barcode markers in PNG format inside your ARToolKit distribution, in the folder "Matrix code 3x3" inside the folder "patterns" inside the folder "doc". You can print these markers using any graphics program.

## Changing the barcode dimensions

If you need more than 64 barcodes, you can change the size of the barcode template. At present, this setting is not adjustable at runtime, so in order to make the change you must edit a configuration file and recompile ARToolKit. If you also use 3x3 barcodes in other projects, its a good idea to make a separate copy of ARToolKit before making the change.

The barcode dimension is set by the values `AR_PATT_SIZE2` and `AR_PATT_SAMPLE_NUM2` in the file `include/AR/arConfig.h`. Set the first value to the number of squares in each dimension, and the second to an integer multiple of the first. The default values are 3 and 9, respectively.

This table shows the number of barcodes possible with each pattern size. In general, it is better to use the smallest pattern size possible, at this helps the patterns be recognised better at a greater distance.

<table rules="all" style="margin:1em 1em 1em 0; border:solid 1px #AAAAAA; border-collapse:collapse;empty-cells:show;" border="2" cellpadding="3" cellspacing="4">

<tbody><tr>
<th> AR_PATT_SIZE2 </th><th> Number of barcodes possible
</th></tr>
<tr>
<td>3 </td><td>64
</td></tr>
<tr>
<td>4 </td><td>8 192
</td></tr>
<tr>
<td>5 </td><td>4 194 304
</td></tr>
<tr>
<td>6 </td><td>8 589 934 592
</td></tr>
<tr>
<td>n </td><td>2^(n*n - 3)
</td></tr>
</tbody></table>

## Format of the multi-marker config file

A multi-marker configuration file is a plain text file which lists the number of markers, followed by a number of entries, each listing:

-   The ID of the marker (where the ID is determined by the 2D-barcode of the marker).
-   The marker's width (in millimeters, or the same unit your camera was calibrated to).
-   The position and orientation of the center of the marker relative to the desired origin of the coordinate system of the whole
    multi-marker set, expressed as the first three rows of an homogenous coordinate transform matrix.

Here is an example, of a multi-marker set formed by 2 80mm markers (IDs 0 and 1) side by side, separated by 40mm, and with the origin of the coordinate system in the middle of the space between them:

<pre>
2

0
80.0
1.0 0.0 0.0 -60.0
0.0 1.0 0.0  0.0
0.0 0.0 1.0  0.0

1
80.0
1.0 0.0 0.0  60.0
0.0 1.0 0.0  0.0
0.0 0.0 1.0  0.0
</pre>

This format is identical to the config file format used for pictorial (template) markers with one obvious exception; a marker number takes the place of the marker pattern file.