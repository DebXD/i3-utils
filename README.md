# i3-utils

## Fix Screen Tearing in i3 on `amdgpu` or `radeon` gpu driver

## Check if you have `amdgpu/radeon` in use

```
lspci -nnk | grep -i -EA3 "3d|display|vga"
```

## \* Use this method you have `amdgpu` or `radeon` gpu used by kernel

## Run this command to check if you have either `xorg.conf` file or `xord.conf.d` folder

```
ls -l /etc/X11
```

### if You have `xorg.conf` file

```
mkdir ~/xorg-backup
sudo cp -v /etc/X11/xorg.conf ~/xorg-backup/
```

### if You have `xorg.conf.d` folder

```
mkdir ~/xorg-backup
sudo cp -v /etc/X11/xorg.conf.d ~/xorg-backup/
```

## For `radeon` gpu

```
sudo nvim /etc/X11/xorg.conf
```

Paste this in that file
```
Section "Device"
        Identifier "Radeon"
        Driver "radeon"
    Option "TearFree" "on"
EndSection
````

## For `amdgpu`

If You don't have `xorg.conf.d` folder then create by this command
```
sudo mkdir /etc/X11/xorg.conf.d
```

```
sudo nvim /etc/X11/xorg.conf.d/20-amdgpu.conf
```

Paste this in that file
```
Section "Device"
        Identifier "AMD"
        Driver  "amdgpu"
        Option "TearFree" "true"
EndSection
```
### Tutorial Video
https://youtu.be/WWg8q_f7nI4
