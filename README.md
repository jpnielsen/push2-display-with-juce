# README #

to build using VS2019, git clone and edit 
 \modules\libusb\libusb\os\threads_windows.h
 
https://github.com/libusb/libusb/issues/755

## Included README from Ableton ##

## About this repository ##

This repository contains C++ source code that demonstrates how to communicate
with Ableton's Push 2 display. The example uses [JUCE](https://www.juce.com/),
allowing the use of all the existing
[juce::Graphics](https://www.juce.com/doc/classGraphics) methods to render the
content of the display. Thanks to JUCE, it is also cross-platform and can be
compiled using MacOS, Windows, and Linux.

Together with our
[Push interface description](https://github.com/Ableton/push-interface), this
enables you to take full control of Push to develop custom software.

To get an idea of what this can allow you to do,
[here's an example video](https://www.youtube.com/watch?v=9HuNeQQoEmM) of
Mutable Instrument's drum sequencer "Grid" running standalone on a Raspberry Pi
driven from a Push 2.


### Note ###

The low-level classes used to communicate with the display are _not_ tied to
JUCE in any way. This means they can be extracted from this example and used in
another framework if desired.


### License ###

This software is distributed under the [MIT License](./LICENSE).


### Dependencies ###

In order to communicate over USB, this example uses
[libusb](http://www.libusb.org/). On MacOS and Windows, libusb is compiled as
part of the example. On Linux, you will need to use your favorite package
manager to install the development package; for example,

`sudo apt-get install libusb-1.0-0-dev`

Note that if you ship an application using libusb, you should ensure that you
respect their
[licensing terms](http://www.gnu.org/licenses/old-licenses/lgpl-2.1.html).

On Linux, you will also need to
[fetch the packages needed for JUCE](https://forum.juce.com/t/list-of-juce-dependencies-under-linux/15121).


## How do I get set up? ##

### Setting up the repository ###

Clone the repo (including the submodules for JUCE and libusb):

`git clone --recurse-submodules https://github.com/jpnielsen/push2-display-with-juce.git`


### Building ###

The example uses the standard JUCE folder structure and, although it doesn't
make any sound, is based on the "Audio Application" template from the
Introjucer.

There are projects ready for Xcode and Visual Studio 2013, as well as a Linux
Makefile-based system, all located in the `Builds` folder.


### Running ###

Once the program is compiled, running it will open a window on the computer's
screen and display an animation on the Push display. As a bonus, the computer
window will display MIDI messages generated by touching the Push 2 pads,
buttons, and knobs.

**Note that by default on Linux, the USB port can only be used by root. Unless
you change the device's permissions, you will need to sudo to execute the
binary.**

`cd Builds/LinuxMakefile/`

`make`

`sudo ./build/juce2push2`


### Customization ###

If you would like to quickly hack some drawing of your own, have a look at the
`Demo::drawFrame()` method in `juce2push2/Source/Push2Demo.cpp`.

### Maintainers ###

