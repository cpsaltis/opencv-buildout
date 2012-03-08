OpenCV buildout
===============

:Version: 0.0
:Author: Chris Psaltis
:Source: https://github.com/cpsaltis/opencv-buildout
:License: BSD
:Keywords: python, zc.buildout, OpenCV, pyopencv, computer vision, machine vision, photogrammetry

Introduction
------------

Building OpenCV and its python bindings can be a pain. This is an attempt to streamline and simplify the process using zc.buildout. This buildout downloads and builds OpenCV and all its dependencies from source, without the need of root access. The user can choose between the default OpenCV python bindings and the pyopencv ones. Note that pyopencv works with OpenCV v2.1.0.

Currently it is tested in Debian based systems, but it should work as it is on almost every Linux distro. It is still untested in MacOS and Windows.

This is work in progress, so there are still dependencies on system packages and many rough edges. In more detail:

- there are still some image handling libraries to be supported,
- ffmpeg and video handling is not supported,
- not tested in systems without GTK,
- it does not include TBB, IPP, Qt and CUDA toolkit,
- for the pyopencv libboost is not build,
- the envrinonment paths are not set automatically,
- how will the system numpy be exposed to the buildout, should it be compiled and add its dependencies here?

Requirements
------------

Before proceeding you'll need some basic packages. In Debian based systems install with::

    $sudo aptitude install build-essential python-dev python-numpy git

- build-essential contains the tools to build C/C++ code,
- python-dev for building python eggs with C code inside,
- numpy is a dependency for OpenCV python bindindings and for pyopencv. It is difficult to include it in the buildout since it requires a C and a FORTRAN compiler to build and has dependencies to LAPACK and ATLAS. Since it comes with binaries for a bunch of platforms is is easier to put is as a requirement. Refer to http://docs.scipy.org/doc/numpy/user/install.html for details on installing numpy.
- git will be used to clone this repository so it is optional

Installation
------------

Simply clone this repository and run buildout.::

    $git clone
    $cd opencv-buildout/
    opencv-buildout$python bootstrap.py -c opencv.cfg
    opencv-buildout$./bin/buildout -v -c opencv.cfg

If you need the pyopencv bindings::

    opencv-buildout$./bin/python bootstrap.py -c pyopencv.cfg
    opencv-buildout$./bin/buildout -v -c pyopencv.cfg

Usage
-----

To run the interpreter with pyopecncv support do::

    LD_LIBRARY_PATH=/home/three/dev/opencv-buildout/parts/opencv/build/lib ./bin/cvpy

and in python::

    import pyopencv as cv

To run the interpreter with the native python bindings copy opencv's dist-packages to the virtualenv's site-packages::

    cp -r parts/opencv/build/lib/python/dist-packages/cv* lib/python2.6/site-packages/

then from cvpy you can::

    import cv, cv2
