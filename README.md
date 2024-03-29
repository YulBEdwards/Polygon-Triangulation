# Polygon-Triangulation
Tutorial application for the study of Berg et al. polygon triangulation algorithms

This application is a tutorial on the algorithms for rapid polygonal triangulation as described in the text, “Computational Geometry” (Berg, Kreveld, Overmars and Schwartzkopf) on pages 45-61. The first step requires implementation of a binary tree. The software for this is an AVL self-balancing tree.

The application is implemented in Lazarus because it can be immediately run on a variety of platforms (Linux, Raspberry Pi, Apple, etc.) without any changes to the software. All that is required is to install the open-source Lazarus software on the target computer. Also, Lazarus is a near-cousin to Microsoft’s C#, so understanding the Lazarus implementation should be quite easy for users of C# software.

The algorithms can accomplish polygon triangulation in O[n log(n)] time. A sort of the polygon data by ascending y coordinate is an [n log(n)] time characteristic. The triangulation is in three steps: 1. The polygon is converted into a set of monotone polygons by defining partition lines. 2. The parameters of the monotone polygons defined by the partition lines are determined, and 3. The monotone subpolygons are triangulated. 

The first step the calculation processes vertices in the polygon from top to bottom, classifying them according to six categories; Start, End, Merge, Split, Regular up and Regular down. The application implements the processing exactly as described in the reference text, and very detailed output is produced to track the calculation. In this step, processing a vertex often involves inserting and/or deleting an item from the binary tree, so this step also has an [n log(n)] characteristic.

The second step uses the partition lines determined in step 1 develop characteristics for the monotone subpolygons. From these lines the topmost points on each monotone subpolygon are obtained. The final step, triangulating each of the monotone subpolygons, follows exactly the algorithm presented in the reference text. 

The application has a parameter to rotate the data. One should notice the different results as the data is rotated.

An option is provided to generate the motorcycle graph of the polygon. The open circles that appear in the graph interior are the so-called "B" points. This point is at the intersection of a vertex bisector and the bisector of an extended edge of the bisector and the target side of the vertex.

NB: The polygon must close counterclockwise; holes need to close clockwise.
