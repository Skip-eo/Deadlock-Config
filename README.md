# Deadlock Config by SKIÞ
Set of optimisations, tweaks and improvements for Valve's Deadlock.

### Table of Contents
- [Steam Launch Options](#steam-launch-options)
- [Auto Exec](#auto-exec)
- [21:9 FOV Increase](#219-fov-increase)
  - [For NVidia GPU's](#for-nvidia-gpus)
  - [For AMD GPU's](#for-amd-gpus)
  - [Deadlock settings](#deadlock-settings)
  - [KNOWN ISSUE: Game freezing on boot](#known-issue-game-freezing-on-boot)


### **!!!Always close the game before making changes!!!**

## Steam Launch Options
Open the launch options for deadlock in steam and add:

```-dx11 -novid -preload -m_rawinput 1 +exec autoexec.cfg``` 

*Unknown if m_rawinput exists in deadlock*

swap -dx11 for -vulkan depending on your hardware config.

## Auto Exec
Add the [autoexec.cfg](/../main/autoexec.cfg) file to your config folder:

```[Your steam install location here]\Steam\steamapps\common\Deadlock\game\citadel\cfg```

Uncomment and change the marked options in the autoexec to fit your preferences.

## 21:9 FOV Increase
Turns out the game currently increases and decreases your horizontal FOV depending on your aspect ratio. By configuring your video.txt file to only reduce your vertical res, but keep your horizontal the same, you can increase your fov by ~20% (from default 75FOV at 16:9 to ~99FOV at 21:9).

### For NVidia GPU's
In Nvidia Control Panel, under "Display" then "Adjust desktop size and position", set scaling mode to "Aspect Ratio" and check "Override the scaling mode set by games and programs"

![Nvidia Control Panel Desktop Resizing](/../main/images/NVCP-Desktop-Sizing.png)

Under "Display" then "Change resolution", open the "Customise" window.

*Note: if greyed out, ensure under "3D Settings" then "Manage 3D settings", that "DSR - Factors" has all options unchecked.

![Nvidia Control Panel Change Res](/../main/images/NVCP-Change-Resolution.png)

In the "Customise" window, ensure "Enable resolutions not exposed by the display" is checked, then open the "Create Custom Resolution" window.

![Nvidia Control Panel Custom Res](/../main/images/NVCP-Custom-Resolution.png)

In the "Create Custom Resolution" window, adjust the "Vertical lines" number to be the 21:9 equivalent of your monitor's native horizontal size. Ensure "Refresh rate (Hz)" matches the maximum refresh rate of your monitor. Then select "Test". If your monitor shows a 21:9 display, congratulations it's all working!

| 16:9 Resolution | 21:9 Equivalent |
| --------------- | --------------- |
| 1280 x 720      | 1280 x 549      |
| 1920 x 1080     | 1920 x 823      |
| 2560 x 1440     | 2560 x 1097     |
| 3840 x 2160     | 3840 x 1646     |

If your listed resolution is not here, simply divide your horizontal resolution (for instance 1920 for a 1920x1080 display) by 21:9 (~2.33333 recurring) and round to the nearest integer.

***Note:*** *i've had one user with a monitor that perpetually showed "out of range" when attempting this, have yet to dive into why/how to fix it. If it happens to you, feel free to reach out.*

![Nvidia Control Panel Custom Res Settings](/../main/images/NVCP-Custom-Resolution-Settings.png)

### For AMD GPU's
TODO

### Deadlock settings
To run the game in 21:9 at the full horizontal size of your display, you'll need to modify your video.txt config file. Natively the game has a set of pre-defined resolutions, so we need to force set our desired un-defined one.

To do this, browse to your deadlock cfg folder:

```[Your steam install location here]\Steam\steamapps\common\Deadlock\game\citadel\cfg```

And open video.txt (note the .txt.bak version) in your desired text editor.

Next, adjust the highlighted settings. 
- "defaultres" is your horizontal display size (shoudln't need modifying)
- "defaultresheight" should be set to the 21:9 equivalent that you set before. 
- "refreshrate_numerator" should be set to your display's refresh rate
- "refreshrate_denominator" should be set to 1
- "fullscreen" should be set to 1*
- "monitor_index" usually should be set to 0**
- "aspectratiomode" should be set to 0***

*See next section

**Index of the display you're using, usually your primary display

***(0 = 16:9, 1 = 16:10, 2 = 21:9)

![Video.txt settings](/../main/images/Deadlock-Video-Config.png)

Next, right click on video.txt, and set the file to "Read-only". Click okay.

![Video.txt read only](/../main/images/Deadlock-Set-Read-Only.png)

Finally, use the windows shortcut "Win + Ctrl + Shift + B" to reboot your graphics drivers. You can now test launching Deadlock!

### KNOWN ISSUE: Game freezing on boot
If the game freezes on boot, use task manager to kill the application (project8.exe), the shortcut "Ctrl + Shift + Esc" can be used to bring up task manager in this event.

Back in your video.txt file, make sure to open properties and uncheck read-only, then change "fullscreen" to 0, "nowindowborder" to 1, and adjust your desktop resolution to the custom 21:9 one we set before. Remeber to recheck read-only!

Currently troubleshooting as why this happens (only some users)
