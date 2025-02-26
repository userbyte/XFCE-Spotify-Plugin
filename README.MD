# XFCE MPRIS Plugin
## Note: this is a fork of https://github.com/macr1408/XFCE-Spotify-Plugin, modified to support all MPRIS2 players, instead of just Spotify via the Spotify Web API.

This plugin integrates MRPIS Now Playing feature with XFCE Panel.

![example](example.png)

## Features

- Shows the current song playing
- On hover, show additional song info (the album name by default)
- Click to open song link in browser
- (Optional) See album art (disabled by default cuz it requires python)

## What are the requirements for this?

- XFCE *(well, technically just the XFCE panel. this plugin should work on any WM/DE the panel will run on)*
- [XFCE Plugin: Genmon (Generic Monitor)](https://goodies.xfce.org/projects/panel-plugins/xfce4-genmon-plugin)
- D-Bus
- Python3 (for image support)

Genmon usually comes in the "xfce4-goodies" package for your distribution.

## Installation

### Installing this plugin
1. Download/clone this repo to somewhere you want the program to live
2. Cd into the folder that was downloaded, then make `xfce-mpris-main.sh` executable: `cd XFCE-MPRIS-Plugin && chmod +x xfce-mpris-main.sh`
3. Create a "Generic Monitor" item on your panel
4. Edit properties of this "Generic Monitor" item to execute the file xfce-mpris-main.sh, hide the label *(or don't, it's up to you lol)*, and set a period of 10 seconds
5. Enjoy!

### Image support (requires python3)

#### To enable album artwork display:

1. Run this command to install the required python dependencies: `python3 -m pip install python-resize-image pillow wget`
2. Change `IMGENABLE` to "true" in config.sh, and optionally (but recommended) edit `IMGSIZE` to match your panel height.

## F.A.Q

### **Can I change the format (ex. Artist - Song Title)?**

Yes. You can edit `OUTFORMAT` in config.sh.

### **Does this plugin show real time info?**

*Technically* it doesn't, but it refreshes every 10 seconds (you can even lower down this number in the genmo settings) so it emulates being in real time

### **But I want real time info about the current playing song, I will lower down the refresh time to 1 second...**

Sure, go for it! Since we're getting the song data locally, we are not limited to how often we can get it. However, keep in mind that you will be setting a series of commands to run every X seconds, so try to set this value to something sensible (especially if you have low-end hardware).

### **What was the motivation for making this fork?**

I was having issues with getting the Spotify API to work, I believe their API has changed causing the original project to break (I don't remember the error). It might work fine... and I may just be stupid, but I spent about an hour reading Spotify docs trying to get it working with no success, and decided using something else would be easier. Using D-Bus directly is a much simpler and cleaner way to get music data.

## Credits

- Genmon for making this possible, and being very easy to work with
- All the StackOverflow community with their answers
- [macr1408](https://github.com/macr1408) for original code, [userbyte](https://github.com/userbyte) to avoid using the Spotify Web API