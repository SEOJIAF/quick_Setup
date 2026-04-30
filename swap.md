you have to add a launch argument into GRUB config so:

```
sudo nano /etc/default/grub
```
find a line like :
```
GRUB_CMD_LINUX_DEFAULT="loglevel=4 "
```
make sure its uncommented so without a # at the start

and just add 
```
GRUB_CMD_LINUX_DEFAULT="loglevel=4 hid_apple.swap_fn_leftctrl=1"
```

you can add 
```
hid_apple.swap_opt_cmd=1 --swaps the option key with cmd
hid_apple swap_fn_leftctrl=1 --swaps the fn key with ctrl
```
