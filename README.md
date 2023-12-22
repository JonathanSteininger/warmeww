# WarmEww

This is a config that uses bash scripts and <a href="https://github.com/elkowar/eww">eww<a/>.

If you want to use this script you will have to change the root directory path to the scripts/spotifyicons directory inside the cacheSpotifyIcons script

<h3>
Things I have made for it
</h3>

<h5>
Spotify
</h5>
using the playerctl cli application I have made a small media player that controls the spotify player and dislpays the songs information and image.
<br>
If you want to play music with it spotify needs to be open so playerctl can interact with it in the background.

<h5>
Audio
</h5>
I made a pop out menu that allows the user to select the output stream and change/mute the volume.
This uses wireplumber with pipewire to get audio devices and change values.


<h5>
Battery
</h5>
This simply uses acpi to gather battery information and display it. The pop out currently displays a more accurate scale of the battery remaining.


<h5>
windowManager
</h5>
this is a CLI bash script I made that interacts with eww to keep track of which window is currently open and uses eww windows to detect if you click off the window to close it.

