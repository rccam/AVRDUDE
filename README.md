# **AVRDUDE - AVR Downloader/UploaDEr**
[AVRDUDE](http://savannah.nongnu.org/projects/avrdude) is a utility to download/upload/manipulate the ROM and EEPROM contents of AVR microcontrollers using the in-system programming technique (ISP).

See the documentation file for the details.

## Documentation

PDF Documentation can be downloaded from the [download area](http://download.savannah.gnu.org/releases/avrdude/), or read online [here](http://www.nongnu.org/avrdude/user-manual/avrdude.html).

## The latest official version of AVRDUDE is always available [here](http://svn.savannah.gnu.org/viewvc/avrdude/trunk/).

### [AUTHORS](https://github.com/rccam/AVRDUDE/blame/master/AUTHORS)

### [RELEASES](http://download.savannah.gnu.org/releases/avrdude/)

### [VERSION DESCRIPTION](https://github.com/rccam/AVRDUDE/blame/master/NEWS)

### [FULL CHANGELOGS](https://github.com/rccam/AVRDUDE/tree/master/doc)

## History

AVRDUDE has once been started by [Brian S. Dean](http://web.archive.org/web/20040509005714/http://www.bsdhome.com:80/) as a private project of an in-system programmer for the Atmel AVR microcontroller series, as part of the Opensource and free software tools collection available for these controllers. Originally, the software was written for the [FreeBSD operating system](http://www.freebsd.org/), maintained in a private CVS repository, and distributed under the name avrprog.

Due to the growing interest in porting the software to other operating systems, Brian decided to make the project publically accessible on [savannah.nongnu.org](http://savannah.nongnu.org/). The name change to AVRDUDE has been chosen to resolve the ambiguity with the avrprog utility as distributed by Atmel together with their AVRstudio software.

## Main features

The major features of AVRDUDE include:

- Command-line driven user interface for all downloading and uploading features (including handling fuse bytes), for easy automation e. g. by inclusion into Makefiles.
- Interactive examination and modification of various memory regions in so-called terminal mode. Also offered is an option to modify the operational parameters of an Atmel STK500 board (target voltage, VAref, master clock frequency).
- Known to run on all major POSIX-style operating systems, as well as Win32 platforms. By using existing operating system drivers on the POSIX-style systems, secure parallel-port access without root privileges can be maintained. On Win32 platforms, parallel port access requires the previous installation of a driver (giveio.sys) that grants a user process direct access to the IO registers.
- Supports a wide range of programming hardware, from cheap ISP plugs that connect the AVR's ISP interface directly to a computer's parallel port (no additional circuitry) or serial port (some additional circuitry needed), more advanced ISP adapters using a buffer/driver chip (like a 74HC373), up to (more complex) serially connected programmers like AVR910-style ISP devices, the Atmel STK500 board, and the Atmel JTAG ICE mkII. Most popular adapters come pre-defined, adding a new parallel-port adapter is as simple as editing a configuration file (no recompilation needed).
- Supports Intel Hex, Motorola S-Record, and raw binary files for input and output, as well as direct memory contents specification on the command-line (useful e. g. for fuse bytes). On input, the file format can be auto-detected.
- In "terminal mode", the device's memory areas can be examined, and possibly modified. This allows to set fuses interactively, or to modify a few EEPROM cells.

## How to get help or report bugs

To get support for AVRDUDE, or get in contact with other users of this tool, see the [avr-chat mailing list](http://lists.nongnu.org/mailman/listinfo/avr-chat).

People who want to contribute in some way to the project can subscribe to the [avrdude-dev mailing list](http://lists.nongnu.org/mailman/listinfo/avrdude-dev), and get in contact with the developer team there.

If you are certain you found a bug in AVRDUDE, you can open a [bug report](https://savannah.nongnu.org/bugs/?group=avrdude).

There is not much developers' documentation for AVRDUDE so far. There is a [Developers' Corner](http://www.nongnu.org/avrdude/developers.html) with some random articles. Some more information is available at [Brian's private site](http://web.archive.org/web/20111113015125/http://www.bsdhome.com/avrdude/).

## BUILD-FROM-SVN

1. svn co svn://svn.savannah.nongnu.org/avrdude/trunk

2. cd trunk/avrdude

3. ./bootstrap

4. ./configure

5. make

Important environment variables for ./configure:
- CPPFLAGS: C preprocessor flags (*not* "C++")
This is the place to put additional (non-standard) -I options into. For example, if your Windows system has LibUSB-Win32 installed into \\WINDOWS\ProgramFiles\LibUSB-Win32, to tell configure where to search for the header files, use:
- CPPFLAGS=-I/WINDOWS/ProgramFiles/LibUSB-Win32/include
(The use of forward slashes rather than backslashes can often simplify things. Note that the Windows system services internally treat both the same. It's only cmd.exe which requires backslashes as the directory separator.)

- LDFLAGS: Linker options
This is the place to make additional library locations known to the linker.  To continue the above example,to make the linker search for "libusb.a" in that directory, use:
- LDFLAGS=-L/WINDOWS/ProgramFiles/LibUSB-Win32/lib/gcc

Linux users: make sure the header files are installed.
  
While many Linux distributions install the libraries needed by AVRDUDE (libusb, libelf) by default, they leave out the corresponding header files.  Consequently, the configure script won't find them, so these libraries could not be used.

Usually, the packages with the header files (and static libraries) are derived from the regular package name by appending "-devel".  Thus, make sure you have "libusb-devel" and "libelf-devel" installed before running the configure script.  (Same goes for libftdi.)


