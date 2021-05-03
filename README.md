# Document Loader

This is the `DocumentLoader` example from LibreOffice SDK, converted to use
`qmake`, in order to compile, execute and debug easier using Qt Creator.

## Compiling and Running

To be able to compile and run this example, you should have installed
LibreOffice and LibreOffice SDK, then you should set `LOROOT` in
`DocumentLoader.pro` to appropriate folder. For LibreOffice 7.1 SDK, you should
use this line:

    LOROOT = /opt/libreoffice7.1

Due to a problem in LibreOffice build for Ubuntu, 
[LibreOffice bug #14186](
https://bugs.documentfoundation.org/show_bug.cgi?id=141896), you have to create
symbolic link `/libmergedlo.so` using this command:

    $ sudo ln -s /opt/libreoffice7.1/program/libmergedlo.so /libmergedlo.so

If you have [built LibreOffice](
https://wiki.documentfoundation.org/Development/BuildingOnLinux) yourself, use
the `instdir` path for `LOROOT`:

    LOROOT = /home/hossein/Projects/libreoffice/core/instdir

In such case, the above symbolic link is not needed, and should not be created.

Compiling and running the `DocumentLoader` example is easy. First, run an
instance of LibreOffice to listen for the incoming connections:

    $ libreoffice7.1 "--accept=socket,port=2083;urp;"
    
and then just open the project file in Qt Creator, and click `Run` or press
`Ctrl+R`.

If you use a local build, run:

    $ ./instdir/program/soffice.bin "--accept=socket,port=2083;urp;"
    
And execute the project from Qt Creator.

## Running from Command Line

To run `DocumentLoader` from command line, go to the build folder, and then:

    $ export LD_LIBRARY_PATH=/opt/libreoffice7.1/program
    $ ./DocumentLoader

And for a local build:

    $ export LD_LIBRARY_PATH=/home/hossein/Projects/libreoffice/core/instdir/program
    $ ./DocumentLoader

## Comparing with the Original DocumentLoader Example

If you have installed LibreOffice 7.1 SDK, all the example with be place at:

    /opt/libreoffice7.1/sdk/examples/
    
The original `DocumentLoader` example can be found at:

    /opt/libreoffice7.1/sdk/examples/cpp/DocumentLoader/
