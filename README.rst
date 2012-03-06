Does not include the optional IPP, Qt and CUDA toolkit. Experimenting with TBB. Stills need all image/video dependencies. No need for cmake package, but still needing libboost-python-dev.

To run the interpreter with pyopecncv support do::

    LD_LIBRARY_PATH=/home/three/dev/pyopencv-buildout/parts/opencv/build/lib ./bin/cvpy

and in python::

    import pyopencv as cv

To run the interpreter with the native python bindings copy parts/opencv/build/lib/python/dist-packages/cv.so and cv2.so to lib/python2.6/site-packages/ an then::

    import cv, cv2
