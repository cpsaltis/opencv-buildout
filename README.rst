Does not include the optional IPP, Qt and CUDA toolkit. Experimenting with TBB. Stills need all image/video dependencies. No need for cmake package, but still needing libboost-python-dev.

To build the default python bindings for OpenCV run::

    ./bin/buildout -v -c opencv.cfg

To build pyopencv bindings for OpenCV run::

    ./bin/buildout -v -c pyopencv.cfg

To run the interpreter with pyopecncv support do::

    LD_LIBRARY_PATH=/home/three/dev/opencv-buildout/parts/opencv/build/lib ./bin/cvpy

and in python::

    import pyopencv as cv

To run the interpreter with the native python bindings copy opencv's dist-packages to the virtualenv's site-packages::

    cp -r parts/opencv/build/lib/python/dist-packages/cv* lib/python2.6/site-packages/

then from cvpy you can::

    import cv, cv2
