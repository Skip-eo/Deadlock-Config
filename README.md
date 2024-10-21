# Deadlock Config by SKIÞ
Set of optimisations, tweaks and improvements for Valve's Deadlock.

# Steam Launch Options
Open the launch options for deadlock in steam and add:

```-dx11 -novid -preload -m_rawinput 1 +exec autoexec.cfg``` 

*unknown if m_rawinput exists in deadlock*

swap -dx11 for -vulkan depending on your hardware config.

# Auto Exec
Add the autoexec.cfg file to your:

[Your steam install location here]\Steam\steamapps\common\Deadlock\game\citadel\cfg folder.

Uncomment and change the marked options in the autoexec to fit your preferences.

# 21:9 FOV Increase
Turns out the game currently increases and decreases your horizontal FOV depending on your aspect ratio. By configuring your video.txt file to only reduce your vertical res, but keep your horizontal the same, you can increase your fov by ~20% (from default 75FOV at 16:9 to ~99FOV at 21:9).

ADD INSTRUCTIONS HERE
