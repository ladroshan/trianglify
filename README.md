[![Build Status](https://travis-ci.com/sdsmdg/trianglify.svg?token=tRURwj39jsSs5JWUTxs6&branch=develop)](https://travis-ci.com/sdsmdg/trianglify)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

<div style="text-align:center"><img src="resources/trianglify-logo-180.png" data-canonical-src="trianglify-logo-180.png" width="154" height="154" /></div>

# Trianglify
Trianglify is an Android library that helps creates views with beautiful patterns. Trianglify is based on MVP architecture and licensed under MIT license

# Usages
> This library is under construction, for usage please check back later.  

TrianglifyView should be invalidated on change of any of the parameter for changes to take effect.  
**Note:** If any of the parameters is changed `TrianglifyView` regenerates every thing from scratch

# Documentation
1. [Example Usages](#1-example-usages)
    1. [Java](#11-java)
    2. [XML](#12-xml)
2. [API Documentation](#2-api-documentation)
    1. [Attributes](#21-attributes)
    2. [Details of Bleed and Grid dimensions](#22-details-of-bleed-and-grid-dimensions)
3. [Performance analysis](#3-performance-analysis)
4. [UML Diagrams](#4-uml-diagrams)

## 1. Example Usages
### 1.1 Java

Import Statements
```
import com.sdsmdg.kd.trianglify.views.TrianglifyView;
import com.sdsmdg.kd.trianglify.models.Palette;
```
Code for using TrianglifyView  
```
a = (TrianglifyView) findViewById(R.id.trianglify_main_view); 
trianglifyView.setGridWidth(trianglifyView.getWidth())
            .setGridHeight(trianglifyView.getHeight())
            .setBleedX(50)
            .setBleedY(50)
            .setCellSize(20)
            .setVariance(10)
            .setTypeGrid(0)
            .setPalette(26)
            .setDrawStrokeEnabled(false);
```
### 1.2 XML
```
<com.sdsmdg.kd.trianglify.views.TrianglifyView
    android:id="@+id/trianglify_main_view"
    app:cellSize="20dp"
    app:variance="10dp"
    app:bleedX="50dp"
    app:bleedY="50dp"
    app:gridType="rectangle"
    app:palette="Spectral"
    app:fillStrokes="true"
    app:fillTriangle="true" />
```
## 2. API Documentation
### 2.1 Attributes
| Property                    | Java method             | XML Attribute       | Description                                                                                                                   |
|-----------------------------|-------------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------------|
| Grid Height                 | .setGridHeight(...)     | grid_height     | Height of the grid to generate                                                                                                |
| Grid Width                  | .setGridWidth(...)      | grid_width      | Width of the grid to generate                                                                                                 |
| X-axis Bleed                | .setBleedX(...)         | bleed_x         | TrianglifyView generates total area having width = gridWidth + 2*bleedX to avoid unfilled triangles at the edges of the view  |
| Y-Axis Bleed                | .setBleedY(...)         | bleed_y         | TrianglifyView generates total area having height = gridWidth + 2*bleedY to avoid unfilled triangles at the edges of the view |
| Variance                    | .setVariance(...)       | variance        | Displacement of points from original grid position to create triangles of different sizes                                     |
| Cell Size                   | .setCellSize(...)       | cell_size       | Size of cells of rectangular grid used to generated vertices of the triangles                                                 |
| Grid Type*                  | .setGridType(...)       | grid_type       | Type of grid 0 for Rectangular                                                                                                |
| Fill Triangles with color** | .setFillTriangle(...)   | fill_triangles  | Fills the triangle generated with color chosen                                                                                |
| Draw strokes                | .setDrawStrokes(...)    | draw_strokes    | Draws triangle's border with neighboring triangle's color                                                                     |
| Color Palette               | .setPalette(...)        | palette         | Set of existing colors to color triangles                                                                                     |
| Random Coloring             | .setRandomColoring(...) | random_coloring | If random coloring is on triangles will be colored randomly instead of linear interpolation                                   |
|                             |                         |                 |                                                                                                                               |                                |

*Current release contains only one GridType accessible with id `0`  
**Current release doesn't support custom color palette however a collection of 9 set of colors is available

<p>

### 2.2 Details of Bleed and Grid dimensions
Following image demonstrates region covered by gridHeight, gridWidth, bleedX and bleedY  
<img src="resources/default_pattern_explained.jpg" data-canonical-src="resources/default_pattern_explained.jpg" width="400" height="400" />

### 2.3 Generates
<img src="resources/default_pattern.jpg" data-canonical-src="resources/default_pattern.jpg" width="300" height="300" />

## 3. Performance analysis
Few notes on performance of Trianglify
* Performance takes a serious hit with decrease in cell size. Time complexity of the algorithm to generate triangles from grid of points is Ω(n*log(n)). Decreasing cell size increases n (number of points on the grid). 
* Performance of coloring is faster on the use of random coloring rather than gradient.

## 4. UML diagrams
Complete UML diagram for the project structures are available as Draw.io link hosted in google drive 
| [Link](https://www.draw.io/?state=%7B%22ids%22:%5B%220Bz_2jvdEtUlrWlB0LXJvRnBQZ0U%22%5D,%22action%22:%22open%22,%22userId%22:%22109172653085429225560%22%7D)  
*(Note that you'll require a google account to access the file, if this is your first time then choose `open with Draw.io` option on top of the browser window. Then scroll to the center of the document to view diagrams)*

# License
Trianglify is licensed under `MIT license`. View [license](LICENSE.md).