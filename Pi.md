# pi4

# overclock

`/boot/config.txt`

```txt
over_voltage=6
arm_freq=2147
gpu_freq=750
```

# misc
- Install vscodium

```sh
$ wget -qO - https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/raw/master/pub.gpg | sudo apt-key add -

$ echo 'deb https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/raw/repos/debs/ vscodium main' | sudo tee --append /etc/apt/sources.list.d/vscodium.list
$ sudo apt update && sudo apt install codium

```

- scim

```txt
scim-tables-zh
```