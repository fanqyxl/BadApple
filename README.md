# BadApple

## does this work for me
if you don't have disk layout v3(boards made after 2021), you cant do this exploit because you have no internet recovery option because disk layout v2 and below has no miniOS

## how to do badapple
1. enter developer mode with ESC+REFRESH+POWER and CTRL+D
2. when you reach the block screen, press ESC+REFRESH+POWER again
3. select Internet Recovery
4. when miniOS loads in, press CTRL+ALT+F3(open the VT3)
5. you now have a shell you can type shit in ykyk

## why does this stupid exploit so ez work
because when you enter developer mode, cros_debug is flipped to 1 in crossystem's logic \
now the devs forgot that the recovery initramfs should always be trusted, whether in developer mode or not \
so they just put code in miniOS where if cros_debug == 1, open a shell in the VT3 \
because of googles oversight, we have a shell in the VT3 whilst enrolled.
<https://source.chromium.org/chromiumos/chromiumos/codesearch/+/main:src/platform2/minios/ramfs/etc/init/debug-tty.conf;drc=a344af8a24700b3395cbaec1ab9b914f5b3d5b85;l=18>

## things to do for badapple
- make a payload script we can load onto a USB stick, then mount in the shell and run the script, e.g. `mkdir /mnt/BadApple && mount /dev/sda1 /mnt/Badapple && /mnt/BadApple/start.sh`
