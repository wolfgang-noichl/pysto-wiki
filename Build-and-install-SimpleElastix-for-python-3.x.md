These are unofficial instructions to build SimpleElastix for python 3.x. These are slightly different steps to the official [instructions to build SimpleElastix for python 2.x](http://simpleelastix.readthedocs.io/GettingStarted.html).

These instructions have been tested with Ubuntu 18.04 (Bionic).

1. Install dependencies
   ```bash
   sudo apt-get install cmake swig monodevelop r-base r-base-dev ruby ruby-dev \
   python python-dev python3 python3-dev tcl tcl-dev tk tk-dev
   ```

2. Download source code and build (note that you need ~4GB per processor, e.g. `make -j4` needs 16GB)
   ```bash
   git clone https://github.com/kaspermarstal/SimpleElastix
   cd SimpleElastix
   mkdir build
   cd build
   cmake -DPYTHON_EXECUTABLE:FILEPATH=/usr/bin/python3 \
   -DPYTHON_LIBRARY:FILEPATH=/usr/lib/x86_64-linux-gnu/libpython3.6m.so \
   -DPYTHON_INCLUDE_DIR:PATH=/usr/include/python3.6m \
   -DBUILD_EXAMPLES=OFF \
   -DBUILD_TESTING=OFF \
   ../SuperBuild
   make -j4
   ```
   In some cases, it seems to be necessary to run `make` twice.
    
3. Add the built SimpleITK with SimpleElastix modules to your python install
   ```bash
   cd SimpleITK-build/Wrapping/Python
   sudo python3 Packaging/setup.py install
   ```
    
From now on, you can import SimpleITK with the SimpleElastix extension into your python code. See the [SimpleElastix README.md](https://github.com/kaspermarstal/SimpleElastix/blob/master/README.md), and [SimpleElastix parameters maps](https://simpleelastix.readthedocs.io/ParameterMaps.html) for details.
