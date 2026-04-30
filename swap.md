 It turns out that the Linux kernel allows this customization:

1)) Edit or create the /etc/modprobe.d/hid_apple.conf file, and add the following two lines:

```
options hid_apple swap_fn_leftctrl=1
options hid_apple swap_opt_cmd=1
```

2)) If you are running an Ubuntu-derived distro, run $ sudo update-initramfs -u so that these configs are set at boot time. (For other distros, see references below).

3)) Reboot.

There you go. The Mac keyboard works like the Dell Latitude keyboard shown in the images.

These customization parameters can be set/unset at run time through the following /sys parameters:
```
/sys/module/hid_apple/parameters/swap_fn_leftctrl
/sys/module/hid_apple/parameters/swap_opt_cmd
```
You can enable or disable each option by something like:
```
echo 1 | sudo tee /sys/module/hid_apple/parameters/swap_fn_leftctrl 
echo 0 | sudo tee /sys/module/hid_apple/parameters/swap_fn_leftctrl
```
(Some Linux distros (e.g. Mint Cinnamon) will allow Option and Command to be swapped through a GUI preference widget. But to swap Fn and Control, the swap_fn_leftctrlkernel parameter was the only solution that I found.)

References

    https://wiki.archlinux.org/title/Apple_Keyboard#Swap_the_Fn_and_left_Control_keys

    https://www.reddit.com/r/AsahiLinux/comments/zmuz5l/is_there_a_way_to_remap_fn_to_ctrl/

    https://www.reddit.com/r/linux_on_mac/comments/1j6pb1l/intersting_files_that_are_usefull/
