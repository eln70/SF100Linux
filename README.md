# SF100Linux
Linux software for Dediprog SF100 and SF600 SPI flash programmers

## Building for Linux
To compile the project, first install required dependencies:
  - libusb-1.0

Change to the directory where the sources are located and build using make:
```bash
$ cd SF100Linux
$ make
```

The resulting binary should be called `dpcmd` and located in the root of the
source tree. There is no install target at the moment.

## Usage
Most basic usage is writing a whole image file to a flash chip:
```bash
$ ./dpcmd --auto image.bin --verify
```

This will automatically detect the chip, read out the chip contents, replace
the ones that differ and perform a read and verification after writing.

For more advanced usage see `dpcmd --help`.

## Building for MacOS
Install brew/homebrew using the instructions here:
https://brew.sh/

Use brew to download and install libusb and pkg-config:
```
% brew install libusb
% brew install pkg-config
```
You might need to add homebrew to your path and softlinks for libusb:
```
PATH="/opt/homebrew/bin:${PATH}"
export PATH
sudo ln -s /opt/homebrew/Cellar/libusb/1.0.27/include/libusb-1.0 /usr/local/include/libusb-1.0
sudo ln -s /opt/homebrew/Cellar/libusb/1.0.27/lib/libusb-1.0.0.dylib /usr/local/lib/libusb-1.0.0.dylib
```
Now, follow the instructions to build for Linux
