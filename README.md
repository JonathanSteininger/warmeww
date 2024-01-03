# WarmEww
<body>
<p>
  This is a config that uses bash scripts and <a href="https://github.com/elkowar/eww">eww<a/>.<br>
  If you want to use this script you will have to change the root directory path to the scripts/spotifyicons directory inside the cacheSpotifyIcons script
</p>
<image src="https://github.com/JonathanSteininger/warmeww/assets/51342815/77023ddc-bac9-4b72-b871-3ef6454f6782">
<div>
  <h3>
    Things to know
  </h3>
  this config uses environment specific tools so if you have a different system utility then you will have to adjust the scripts.
  I will list the things each section uses.<br>
  <br>
  I added variables at the top of the eww.yuck config file to disable entire widgets if you don't want to use some.
</div>

<div>
  <h3>
    List of requirements
  </h3>
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
    <li>TPL - a power profile manager for laptops</li>
    <li>polkit (with an agent) - needed for some actions that require super user, like changing min fan speed, changing TPL power mode, or restarting services</li>
    <h4>stuff you will need to configure garenteed</h4>
    <li>lm_sensors (need to configure json output with scripts/getSensors) (also need to configure which fans to display and theire names</li>
  </ul>
</div>

<h3>
  Things I have made for it
</h3>
<ul>
  <li>
    <h5>
      Workspaces
    </h5>
    displays all active workspaces an the windows in them. need to install arcticons icon pack for best results.<br>
    If you want to use other custom icon packs in the getIconPath script add it to the first position of mainCatagory array, it prioritises the start of the array for catagories.<br>
    If the none of the catagory/iconpacks are found it will try to find any matching icon.<br>
    The icons get cached into "scripts/iconCache/". If you want to change the icon pack or need to force an icon to change. remove it from the directory 
    <p style="color: gray;">
      uses: hyprland, jq, head, (recommended) arcticons
    </p>
  </li>
  
  <li>
    <h5>
      Spotify
    </h5>
    <p>
      using the playerctl cli application, I made a small media player that controls the spotify player and dislpays the songs information and image. <br>
      If you want to play music with it spotify needs to be open so playerctl can interact with it in the background.
    </p>
    <p style="colour:blue;">
      Uses: playerctl, spotify-launcher
    </p>
  </li>
  
  <li>
    <h5>
      Sensors & Fans
    </h5>
    <div>
      <p>
        This is a popout that displays your current left and right fan speeds and allows you to force a minimum fan speed.<br>
        The sensor list will need to be manually configured per machine. the json input that it uses is:
      </p>
      <p>
        The general section groups the sensors in 15 sensor chunks so you can display columns of them when you have alot.
      </p>
      <p style="color: gray">
        Uses: jq, lm_sensors
      </p>
    </div>
  </li>

```json
{
  "cpu": [
            {"name": "[core sensor name]", "temps": {"current": 00.0, "hot": 00.0, "critical": 00.0}},
            "..."
  ],
  "gpu": [
            {"name": "sensor name", "temps": {"current": 00.0, "critical": 00.0}},
            "..."
  ],
  "general": [
            [ {"name": "sensor name", "temp": 00.0}, "..."],
            "..."
  ]
}
```
  
  <li>
    <h5>
      Power Profile Selection
    </h5>
    <p>
      This simply restart TPL in the selected mode (audo | ac | bat) uses polkit pkexec to get privileges
    </p>
    <p style="color: gray">
      Uses: tlp, polkit
    </p>
  </li>

  <li>
    <h5>
      Wifi
    </h5>
    <p>
      This uses a script I made to return an json object to eww. looks for a fixed wlan interface (wlan0) if you want to change it edit "scripts/wifi" "wifiInterfaceName=wlan0" to your interface. <br>
      The wifi settings button redirects you to iwgtk. change it to a different application if you prefer.
    </p>
    <p style="color: gray">
      Uses: iwctl from iwd, iwgtk (only for the settings button)
    </p>
  </li>
  
  
  <li>
    <h5>
      Networking
    </h5>
    Displays the total network upload and download rate on the menuBar.<br>
    The Networking panel displays every networking interface and total in a custom graph over time. (20 seconds, 1 second polls) <br>
    This should require no configuration and should update dynamically.<br>
    <p style="color: rgb(50,50,50)">
      uses: ifstat, jq, head
    </p>
  </li>
  
  <li>
    <h5>
      Audio
    </h5>
    I made a pop out menu that allows the user to select the output stream and change/mute the volume.
    This uses wireplumber with pipewire to get audio devices and change values.
    <p style="color: gray">
      uses: pipewire, wireplumber, bc
    </p>
  </li>
  
  
  <li>
    <h5>
      Battery
    </h5>
    This simply uses acpi to gather battery information and display it. The pop out currently displays a more accurate scale of the battery remaining.
    <p style="color: gray">
      uses: acpi
    </p>
  </li>
  
  <li>
    <h5>
    System Performance
    </h5>
    displays the average load and memory usage of the system. can be expanded to show information on every core and more precise memory usage.
    <p style="color: gray">
      uses: uses magic variables, so might not work on macOS
    </p>
  </li>
  
  <li>
    <h5>
      Brightness
    </h5>
    Added brightness controls for the keyboard backlightn and monitor. will need to set MONITOR_BACKLIGHT and KEYBOARD_BACKLIGHT evironment variables. <br>
    eg. export them in your .bashrc file.
    <p style="color: gray">
      uses: brightnessctl
    </p>
  </li>
  
  <li>
    <h5>
      windowManager
    </h5>
    this is a CLI bash script I made that interacts with eww to keep track of which window is currently open and uses eww windows to detect if you click off the window to close it.
  </li>
</ul>
</body>
