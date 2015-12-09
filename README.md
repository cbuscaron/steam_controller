# steam_controller

sudo nano /lib/udev/rules.d/99-steam-controller-perms.rules

then add the following contents, don't forget to use YOUR username in the file!

This rule is needed for basic functionality of the controller in Steam and keyboard/mouse emulation.

SUBSYSTEM=="usb", ATTRS{idVendor}=="28de", MODE="0666"

This rule is necessary for gamepad emulation; 
make sure you replace 'YOUR_USERNAME' with the username of the user that runs Steam

KERNEL=="uinput", MODE="0660", GROUP="YOUR_USERNAME", OPTIONS+="static_node=uinput"

Give the controller access to /dev/uinput
For quick and dirty, sudo chmod 666 /dev/uinput
For a workaround that survives reboots: sudo apt-get install python3-autopilot Then log out/in or reboot. This will add you to a group that has write access to /dev/uinput. This will add a few packages which you probably won't need, but you can remove them once the steam package update arrives.
