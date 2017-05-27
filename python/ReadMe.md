# Boost-Voronoi-For-ArcGIS (Python)

## Description

This section contains a geoprocessing tool. This tool will require the deployement of pyvoronoi 1.0.0. The documentation for installing pyvoronoi is available on project web page: https://github.com/Voxel8/pyvoronoi

For information about the voronoi solver, please refer to the Boost API: http://www.boost.org/doc/libs/1_59_0/libs/polygon/doc/voronoi_diagram.htm

### ArcGIS Desktop

The python package used by this extensions is built on C++ code, which can be unsettling for non-programmers as it requires installing a C++ compiler ([see here for details](https://wiki.python.org/moin/WindowsCompilers))
Since ArcGIS Desktop uses Python 2.7 and works exclusively on Windows, I have attached the compile code packages in the directory pyvoronoi-wheels. In order to install from the wheels you can:

* Double click on the exe file and install pyvoronoi in the python installation used by your ArcGIS environement.

* Open a command line in your python Scripts directory (by default: C:\Python27\ArcGIS10.3\Scripts) and yype the following in a command line: ``pip install pyvoronoi==1.0.3``

The wheels are built for 32 and 64 bits environements.

If you already have a C++ compiler, are on a Linux OS, or are using another version than Python 2.7, you will need to install from Pypi.

``pip install pyvoronoi==1.0.3``

Consult the help of associated with the geoprocessing tools for more information. The pyovornoi github repository has also extensive documentation about installation. 

### ArcGIS Pro 1.3 and 1.4

ArcGIS Pro comes with conda, which means the end-user does not need to deal with all the steps for ArcGIS Desktop installation.

* Open a command line as admin and use the command: cd "C:\Program Files\ArcGIS\Pro\bin\Python\Scripts"

* type: conda install anaconda-client

* conda install -c fabanc pyvoronoi

* Open your ArcGIS Pro Project

* Click on the tab ``Project``

* Click on ``Add Package`` and choose pyvoronoi

* Check the list of installed package to see if pyvoronoi appears in the list.


## Installing Setup tools in Python.

If you choose to install from source or from an off-line environement, you will need to install from source. For that, you will need setup tools: https://pypi.python.org/pypi/setuptools

In order to install, do the following:

* Download setuptools-XX.X.X.zip from https://pypi.python.org/pypi/setuptools

* Extract it in a directory

* Open a command prompt from the start menu or windows explorer

* Install by running this command (replace setuptools-XX.X.X with the appropriate version number. For example setuptools-31.0.1): %ArcGISPythonDirectory%\python.exe %PathToSetupTools%\setuptools-XX.X.X\setup.py install

## Limitations

The output feature class (vertices, edges, cells) may not be exactly snapped to the input line feature class. The reason for that is that the underlying Boost API takes integer as an input. When the coordinates are sent to the voronoi API, they get rounded. There are different strategies we have implemented to fix that issues depending on the level of license in ArcGIS Desktop. One of the solution is to use snappping.

The results of this tool is highly depending on the quality of your input data. It is up to validate that your input data meet the following requirements:

* Input points and line feature class use the same coordinate system.

* Input data is properly snapped. 

* No segments overlap each other.

Having invalid data usually result in the following outcome:

* Pyvoronoi never solves. Pyvoronoi is fast, and bulild the output structure for a million of input points and segments in less than a minute usually. If it lasts longer than that, it is a bad sign.

* The output data is outside of the extent of the input data, or throws an exception saying that the coordinates returned by pyvoronoi are outside of the limit of the projection system.


