Sonify raw video data using Midi CCs and multichannel processing with Ecasound & FFmpeg :^)

# Usage
Syntax: ./glitchcam WIDTHxHEIGTH colorspace audiosamplerate ffaudioformat ecaaudioformat fx1=0 fx2=0

e.g. `./glitchcam 640x360 xyz12le 44100 mulaw 16 fx1=17 fx2=36`

# Requirments

v4l-utils - `sudo apt-get install v4l-utils`

FFmpeg - `sudo apt-get install ffmpeg`

Rosegarden - `sudo apt-get install rosegarden`

ladspa-sdk - `sudo apt-get install ladspa-sdk` <-- ladspa header file thing needed for ecasound to be ladspa compatible

Alsa Lib shared library - `sudo apt-get install libasound2`<-- I needed this to make eca work with my Alsa Sequencer.

Ecasound - `http://nosignal.fi/ecasound/download.php` <-- configure source with `./configure --enable-shared --enable-alsa -enable-ladspa`

Audacity - `sudo apt-get install audacity`

Tap-Plugins - `sudo apt-get install tap-plugins`

A webcam - `Walmart`
 
You may need to move some ladspa plugins from `/usr/lib/ladspa` to `/usr/local/lib/ladspa` or vice versa.
Then in a terminal enter `echo "ladspa-register" | ecasound -c` to make sure ecasound picks up your plugins.

If you don't have a webcam well its pretty ez to edit the source for an input file :>

# Tips & Tricks

Due to some weird bash bug FFmeg likes to hang sometimes. Have `killall -s SIGKILL ffmpeg` ready lol.

Some colorspaces require specific sample rates and audio formats like 16bit or 32bit to not be slow asf (e.g `ffmpeg -i blah -f u16le`)
