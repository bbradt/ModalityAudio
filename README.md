# Welcome to EdgeMidi v 0.0.1
**Author: Bradley Baker**

*Currently in development.*

## Version History:
	0.0.1 - Initial Development Version
	0.0.2 - Added more flexible support for scales, and support of spectrogram img-encoding

## Description

This tool is going to be part of a larger toolbox including some of my previous work on Image->Audio mappings.  

Feedback and ideas are welcome, but keep in mind, many features are already planned, just still in development.

The aim of this simple Python module is to create a program which uses Edge-Detection to generate Midi-Tracks 
which can be inserted into any Midi-Player, or played on the system. 

The idea is to move away from Image-to-Music kits which use RGB values of pixels as input and to instead incorporate 
spatial information about images to generate music. One intuitive way to do this is to use edge information which maps to 
values on a virtual keyboard. 

Midi works most simply in two dimensions - the Pitch (Y) dimension, and the Time (X) dimension. There are additional 
dimensions given in the intensity of the strike on the virtual keyboard and in the channel chosen, etc; however, the simpleest
mapping imagines these values as pre-determined constants, such that the MIDI functionality involves some mapping of 
pitches over time. 

Similarly images at their most basic have two spatial dimensions, an X and Y spatial axis. The idea of this program is 
thus spatial information given in an image to create a mapping from the image into this basic MIDI-space. There are 
many potential mappings from the image-space into MIDI-basic-space and into other MIDI spaces; however, one simple 
mapping uses a binary-spatial-indicator to detect whether or not an image is present at a given spatial coordinate in an 
image, and if so, adds a positive binary indicator to the same coordinate in the MIDI-basic-space. 

To put it simply, we imagine that the MIDI-basic-space of pitches over time is placed as a grid over an image. Then, wherever
we detect an edge in the image at a coordinate (x,y), we indicate that pitch (y) should be played at time (x). 

This software performs 2 basic functions:
	1) Edge Detection (still in development - using 3rd party libraries)
	2) Edge -> MIDI mapping 
	
Beyond these basic functions, there is the included functionality of mapping images to particular Musical Keys.


Features Currently Supported:
	Version 0.0.2:
		MIDI mapping and output for Images already Edge-Detected
		All MAJOR scales
		All MINOR scales
		GNU-style Command-Line arguments for: 
			Adjusting resolution of grid
			Input/Output
			Turning debugging on/off
			more 
		Pitch-Grid Debugging Outputs
		Customizeable Config File
		Spectrogram Analysis, based on [alexodan's img-encode library](https://github.com/alexadam/img-encode)
	
Features in Development:
	On-the-Fly Pitch-Wav / Midi-Wav conversion using only scipy tools
	Dynamic scales and key selection and quantization

Features coming:
	On-the-Fly Edge Detection 
	Unit Tests
	Image-Format Tests
	More command line arguments:
		Adjust MIDI Tempo
		Adjust MIDI Volume
	Alternative Octave-Grid Wrapping Choices
	Dynamic Image Transformation : 
	Auto-Playback
	Generation of Video including time-marker showing pitch-playback 
	GUI 
	Auto-Dependency Check/Installation
	More Scales
		Full Harmonic Scales
		All augmented/diminished keys
		All modes for major/minor keys
		Blues scales
		Jazz scales 
		...
	
Usage: 
	Required Packages:
		You will need to install the following python libraries prior to usage:
			numpy
			scipy	
			pillow
		You are best of doing this by the command line: eg. $python -m pip install numpy 

	The tool is used only via the command line currently. A GUI is on the TODO list.
	For now, the tool can be used via the command:
		$python EdgeMidi.py -i <inputfile> 
	
	For additional flags and arguments via the command line, type 
		python EdgeMidi.py -h 