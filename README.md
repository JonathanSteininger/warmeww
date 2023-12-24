# WarmEww

This is a config that uses bash scripts and <a href="https://github.com/elkowar/eww">eww<a/>.

If you want to use this script you will have to change the root directory path to the scripts/spotifyicons directory inside the cacheSpotifyIcons script

<h3>
Things to know
</h3>
this config uses environment specific tools so if you have a different system utility then you will have to adjust the scripts.
I will list the things each section uses.

<h3>
Things I have made for it
</h3>

<h5>
Workspaces
</h5>
Lists the workspaces with the ability to switch between them. sorts them and only shows the main monitors workspaces.
<p style="color: gray">
uses: hyprland, jq 
</p>


<h5>
Spotify
</h5>
using the playerctl cli application I have made a small media player that controls the spotify player and dislpays the songs information and image.
<br>
If you want to play music with it spotify needs to be open so playerctl can interact with it in the background.
<p style="color: gray">
Uses: playerctl
</p>

<h5>
Audio
</h5>
I made a pop out menu that allows the user to select the output stream and change/mute the volume.
This uses wireplumber with pipewire to get audio devices and change values.
<p style="color: gray">
uses: pipewire, wireplumber, bc
</p>


<h5>
Battery
</h5>
This simply uses acpi to gather battery information and display it. The pop out currently displays a more accurate scale of the battery remaining.
<p style="color: gray">
uses: acpi
</p>

<h5>
System Performance
</h5>
displays the average load and memory usage of the system. can be expanded to show information on every core and more precise memory usage.
<p style="color: gray">
uses: uses magic variables, so might not work on macOS
</p>

<h5>
Brightness
</h5>
Added brightness controls for the keyboard backlightn and monitor. will need to set MONITOR_BACKLIGHT and KEYBOARD_BACKLIGHT evironment variables. <br>
eg. export them in your .bashrc file.
<p style="color: gray">
uses: brightnessctl
</p>

<h5>
windowManager
</h5>
this is a CLI bash script I made that interacts with eww to keep track of which window is currently open and uses eww windows to detect if you click off the window to close it.
<p style="color: gray">
note: you will need to change "openWindowPath" in the bash file!
</p>

