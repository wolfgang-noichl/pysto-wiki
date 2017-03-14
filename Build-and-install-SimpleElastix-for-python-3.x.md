These are unofficial instructions to build SimpleElastix for python 3.x. These are slightly different steps to the official [instructions to build SimpleElastix for python 2.x](http://simpleelastix.readthedocs.io/GettingStarted.html). 

1. Install dependencies

       sudo apt-get install cmake swig monodevelop r-base r-base-dev ruby ruby-dev \
       python python-dev python3 python3-dev tcl tcl-dev tk tk-dev

1. Download source code and build (note that you need ~4GB per processor, e.g. `make -j4` needs 16GB)

       git clone https://github.com/kaspermarstal/SimpleElastix
       cd ~/Software/SimpleElastix
       mkdir build
       cd build
       cmake -DPYTHON_EXECUTABLE:FILEPATH=/usr/bin/python3 \
       -DPYTHON_LIBRARY:FILEPATH=/usr/lib/x86_64-linux-gnu/libpython3.5.so \
       -DPYTHON_INCLUDE_DIR:PATH=/usr/include/python3.5 \
       -DBUILD_EXAMPLES=OFF \
       -DBUILD_TESTING=OFF \
       ../SuperBuild
       make -j4
    
1. Add the built SimpleITK with SimpleElastix modules to your python install

       cd SimpleITK-build/Wrapping/Python/Packaging
       sudo python3 setup.py install
    
From now on, you can import SimpleITK with the SimpleElastix extension into your python code. See the [SimpleElastix README.md](https://github.com/kaspermarstal/SimpleElastix/blob/master/README.md), and [SimpleElastix parameters maps](https://simpleelastix.readthedocs.io/ParameterMaps.html) for details.
