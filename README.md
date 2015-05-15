snap7
=====

CMake based fork of [Snap7](http://snap7.sourceforge.net/).

LIMITATIONS
-----------

Currently there are some limitations derived from the original snap7:
 * On Windows only MSVC is supported
 * Only shared libraries can be built

We also removed Solaris support for now to make the porting to cmake easier.

INSTALLATION
------------

You can build the project using these command:

    git clone https://github.com/autinitysystems/snap7.git
    mkdir snap7/build
    cd snap7/build
    cmake -DCMAKE_BUILD_TYPE=Release ..
    make
    make install

The `make install` might require administrative permissions.
If you want to build the examples you may add `-DWITH_EXAMPLES=ON` to the cmake line.

LICENSE
-------

LGPL version 3.0 (See lgpl-3.0.txt or [LGPLv3](http://www.gnu.org/licenses/lgpl.html))

