Oregon Scientific WMR100 client for Linux/BSD/etc.
==================================================

Supports
--------

Oregon Scientific WMR100
Oregon Scientific WMR200
Oregon Scientific RMS300A

Introduction
------------

The WMR100/200 use a proprietary protocol for their USB
connection. It's very useful for enthusiasts running a headless Linux
box to collect and analyze data from this link, but unfortunately the
protocol isn't openly documented, nor are clients provided for this
platform.

This simple C program handles the USB protocol of the WMR100, and
translates it an ASCII line-format, easy for parsing/analysing.

You'll need to setup the udev rules (see udev/README) if you want to
run this not as root. This is due to how libhid accesses the USB
ports.

This fork add support to sqlite logging

Requisites
----------

libhid-dev (or similarly named) package installed.
pkg-config package installed.
libsqlite3-dev package installed.
libusb-dev package installed.

Building
--------

Run 'make'.

To install, copy wmr100 to your path.

*One time install for osx*
To keep the default HIDManager from taking the wmr100, run this once: `make setup_osx`
If you want to use different software to read the wmr100 device, you should undo this by running
`make unsetup_osx` and then reboot so that the HIDManager will take control of the device again.

To install on raspberry pi use this script : https://github.com/think-free/pi-scripts/raw/master/InstallWmr100OnPi.sh

Usage
-----

I'd suggest you run ./wmr100, which will dump data to data.log as well
as stdout. You can then process periodically data.log with a script in
python/perl/ruby/your language of choice, and frob with the data that
way.

Alternativally you could adapt the original C code to write to a
database directly instead, but that's more pain that I'm willing to
endure. :-)
