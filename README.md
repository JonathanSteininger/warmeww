# WarmEww

This is a config that uses bash scripts and <a href="https://github.com/elkowar/eww">eww<a/>.

If you want to use this script you will have to change the root directory path to the scripts/spotifyicons directory inside the cacheSpotifyIcons script

<h3>
Things to know
</h3>
this config uses environment specific tools so if you have a different system utility then you will have to adjust the scripts.
I will list the things each section uses.
<h3>
List of requirements
<h3>
<ul>
<li>jq</li>
<li>hyprland</li>
<li>playerctl</li>
<li>ifstat</li>
<li>pipewire + wireplumber</li>
<li>bc</li>
<li>brightnessctl</li>
<li>arcticons (dont need it but looks better with it, might need to clear icon cache if installing after running)</li>
<li>head (should be in base linux GNU)</li>
</ul>

<h3>
Things I have made for it
</h3>

<h5>
Workspaces
</h5>
displays all active workspaces an the windows in them. need to install arcticons icon pack for best results.<br>
If you want to use other custom icon packs in the getIconPath script add it to the first position of mainCatagory array, it prioritises the start of the array for catagories.<br>
If the none of the catagory/iconpacks are found it will try to find any matching icon.<br>
The icons get cached into "scripts/iconCache/". If you want to change the icon pack or need to force an icon to change. remove it from the directory 
<p style="color: gray">
uses: hyprland, jq, head, (recommended) arcticons
</p>


<h5>
Spotify
</h5>
using the playerctl cli application, I made a small media player that controls the spotify player and dislpays the songs information and image.
<br>
If you want to play music with it spotify needs to be open so playerctl can interact with it in the background.
<p style="color: gray">
Uses: playerctl
</p>

<h5>
Networking
</h5>
Displays the total network upload and download rate on the menuBar.<br>
The Networking panel displays every networking interface and total in a custom graph over time. (20 seconds, 1 second polls) <br>
This should require no configuration and should update dynamically.<br>
<p style="color: gray">
uses: ifstat, jq, head
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
