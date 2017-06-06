# Boost Voronoi for ArcGIS

## Description

This project provides a set of tools for generating voronoi diagrams based on lines and points. All the tools rely on wrappers around the boost voronoi library http://www.boost.org/doc/libs/1_59_0/libs/polygon/doc/voronoi_diagram.htm.
The plan of this project is to provides tools that can be used in ArcGIS Pro and ArcGIS Desktop in order to generate voronoi cells from line and / or points input. I will be focusing on the developement of python tools first. C# project
might come later but I need to assert if they really bring an additional value. Geoprocessing tools can be called in batches and from the UI whereas add-in can be called only from a UI so I am not sure there is really a point in doing Add-Ins.

## Overview

Here is a screeenshot of what the output look like. Black segments and points are the voronoi input geometries while the cells and cell's vertices are represented in blue.:

![Voronoi Problem](ressources/VoronoiResults.PNG?raw=true "Voronoi Problem")

## Connected Projects

* Pyvoronoi. Originally developed by Voxel8, I have been contributing to it so that it can be used with GIS. The link to the project is https://github.com/Voxel8/pyvoronoi

* SharpBoostVoronoi: developed to support the developement of a geoprocessing tool in C# for an internal code contest at Esri Canada https://github.com/fabanc/SharpBoostVoronoi

## License

The code is available under [MIT license](http://opensource.org/licenses/MIT>).