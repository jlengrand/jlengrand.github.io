---
layout: post
status: publish
published: true
title: Installing gdal for Python 3.6
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: http://www.lengrand.fr
categories:
- work
- fun
- development
tags:
- bash
- experiment
- python
- work
- startup
- hack
- gdal
- gis
- osgeo
comments: []
---

Heyo, 

At **[Skyai](http://skyai.io/)**, we are working a lot with [Geographic Information Systems](https://en.wikipedia.org/wiki/Geographic_information_system).
Just like the large majority of the market, we use [GDAL](http://www.gdal.org/) and its Python bindings for that. 

Even though we are ESRI partners, we still love our QGis and Python.

I recently changed laptop and got the latest Macbook, and had to reinstall the environement from scratch. And as much as I love Python, having to setup GDAL on my former laptop still give me nightmare so I was dreading this moment.


But actually, I have to admit that the process was much smoother than expected! I initially followed [this guide](https://hackernoon.com/install-python-gdal-using-conda-on-mac-8f320ca36d90) for Python 2.7, without success.

But without further due, here are the steps.


## Installing GDAL on Python 3.6


### My setup

* Latest MacBook Pro
* Python 3.6 (but should work for others too)
* conda 4.5.4

### Installing Conda

Simply follow [the official guide](https://conda.io/docs/user-guide/getting-started.html).

### Creating an environment with GDAL as a dependency

```
$ conda create --name gdal_test_working -c conda-forge python=3.6 gdal
```

Accept the request in your terminal : 

```
Solving environment: done

## Package Plan ##

  environment location: /Users/jlengrand/miniconda3/envs/gdal_test_working

  added / updated specs:
    - gdal
    - python=3.6


The following packages will be downloaded:

    package                    |            build
    ---------------------------|-----------------
    poppler-data-0.4.9         |                0         3.5 MB  conda-forge
    certifi-2018.4.16          |           py36_0         142 KB  conda-forge
    libgdal-2.2.4              |                3        14.4 MB  conda-forge
    setuptools-39.2.0          |           py36_0         550 KB  conda-forge
    ------------------------------------------------------------
                                           Total:        18.7 MB

The following NEW packages will be INSTALLED:

    boost:           1.66.0-py36_1         conda-forge
    boost-cpp:       1.66.0-1              conda-forge
    bzip2:           1.0.6-1               conda-forge
    ca-certificates: 2018.4.16-0           conda-forge
    cairo:           1.14.10-0             conda-forge
    certifi:         2018.4.16-py36_0      conda-forge
    curl:            7.60.0-0              conda-forge
    expat:           2.2.5-0               conda-forge
    fontconfig:      2.12.6-0              conda-forge
    freetype:        2.8.1-0               conda-forge
    freexl:          1.0.5-0               conda-forge
    gdal:            2.2.4-py36_0          conda-forge
    geos:            3.6.2-1               conda-forge
    geotiff:         1.4.2-1               conda-forge
    gettext:         0.19.8.1-0            conda-forge
    giflib:          5.1.4-0               conda-forge
    glib:            2.55.0-0              conda-forge
    hdf4:            4.2.13-0              conda-forge
    hdf5:            1.10.1-2              conda-forge
    icu:             58.2-0                conda-forge
    jpeg:            9b-2                  conda-forge
    json-c:          0.12.1-0              conda-forge
    kealib:          1.4.7-4               conda-forge
    krb5:            1.14.6-0              conda-forge
    libdap4:         3.18.3-2              conda-forge
    libffi:          3.2.1-3               conda-forge
    libgdal:         2.2.4-3               conda-forge
    libgfortran:     3.0.1-h93005f0_2
    libiconv:        1.15-0                conda-forge
    libkml:          1.3.0-6               conda-forge
    libnetcdf:       4.6.1-2               conda-forge
    libopenblas:     0.2.20-hdc02c5d_4
    libpng:          1.6.34-0              conda-forge
    libpq:           9.6.3-0               conda-forge
    libspatialite:   4.3.0a-19             conda-forge
    libssh2:         1.8.0-2               conda-forge
    libtiff:         4.0.9-0               conda-forge
    libxml2:         2.9.8-0               conda-forge
    ncurses:         5.9-10                conda-forge
    numpy:           1.14.3-py36he6379a5_1
    numpy-base:      1.14.3-py36h7ef55bc_1
    openjpeg:        2.3.0-2               conda-forge
    openssl:         1.0.2o-0              conda-forge
    pcre:            8.41-1                conda-forge
    pip:             9.0.3-py36_0          conda-forge
    pixman:          0.34.0-2              conda-forge
    poppler:         0.61.1-3              conda-forge
    poppler-data:    0.4.9-0               conda-forge
    proj4:           4.9.3-5               conda-forge
    python:          3.6.5-1               conda-forge
    readline:        7.0-0                 conda-forge
    setuptools:      39.2.0-py36_0         conda-forge
    sqlite:          3.20.1-2              conda-forge
    tk:              8.6.7-0               conda-forge
    wheel:           0.31.0-py36_0         conda-forge
    xerces-c:        3.2.0-0               conda-forge
    xz:              5.2.3-0               conda-forge
    zlib:            1.2.11-h470a237_3     conda-forge

Proceed ([y]/n)? y
```

### Testing the installation

Activate your newly created environment, start python and try to import GDAL

```
$ conda activate gdal_test_working
(gdal_test_working) $ python
Python 3.6.5 | packaged by conda-forge | (default, Apr  6 2018, 13:44:09)
[GCC 4.2.1 Compatible Apple LLVM 6.1.0 (clang-602.0.53)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import gdal
>>> help(gdal)
```

Enjoy!


### The secret

The magic secret is to make sure to use a single forge to install all your dependencies with conda.
In my case I used `-c conda-forge`.

This will ensure there are no possible conflicts between version.

## More about the issue

The first thing I tried was to install without the forge option like this : 

```
$ conda create --name gdal_test python=3.6 gdal
```

But when trying to import gdal, here is the issue I was getting: 

```
$ conda activate gdal_test
(gdal_test) $ python
Python 3.6.5 | packaged by conda-forge | (default, Apr  6 2018, 13:44:09)
[GCC 4.2.1 Compatible Apple LLVM 6.1.0 (clang-602.0.53)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import gdal
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/Users/jlengrand/miniconda3/envs/gdal_test/lib/python3.6/site-packages/gdal.py", line 2, in <module>
    from osgeo.gdal import deprecation_warn
  File "/Users/jlengrand/miniconda3/envs/gdal_test/lib/python3.6/site-packages/osgeo/__init__.py", line 21, in <module>
    _gdal = swig_import_helper()
  File "/Users/jlengrand/miniconda3/envs/gdal_test/lib/python3.6/site-packages/osgeo/__init__.py", line 17, in swig_import_helper
    _mod = imp.load_module('_gdal', fp, pathname, description)
  File "/Users/jlengrand/miniconda3/envs/gdal_test/lib/python3.6/imp.py", line 243, in load_module
    return load_dynamic(name, filename, file)
  File "/Users/jlengrand/miniconda3/envs/gdal_test/lib/python3.6/imp.py", line 343, in load_dynamic
    return _load(spec)
ImportError: dlopen(/Users/jlengrand/miniconda3/envs/gdal_test/lib/python3.6/site-packages/osgeo/_gdal.cpython-36m-darwin.so, 2): Library not loaded: @rpath/libpoppler.71.dylib
  Referenced from: /Users/jlengrand/miniconda3/envs/gdal_test/lib/libgdal.20.dylib
  Reason: image not found
>>>
```

In the end the trick is pretty simple, but it took me a while to find out. 
Hope it helps you too!

Now, back to coding

Cheers, 
Julien