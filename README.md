# BadApple
Patched somewhere around KV4
skid friendly explanation: this allows you to run cryptosmite, icarus and daub on your keyrolled device. It allows for pencil method too.

## What Does This Do??
Badapple is code execution in developer mode in recovery mode. This is basically an exploit that has the same capabilities as Sh1mmer, except that the TPM is disabled.

why? 

refer to this: <https://source.chromium.org/chromiumos/chromiumos/codesearch/+/main:src/platform/depthcharge/src/vboot/load_kernel.c;drc=081580ab61e5b5d4df9389bfe3f9f8891a950c9a;l=116>

## I Have Sh1mmer, This Is Useless
this exploit is only intended for boards that have been keyrolled. e.g. nissa, corsola, dedede.

## Will Badapple Work For Me?

If you don't have disk layout v3(boards made after 2021), you cant do this exploit because you have no internet recovery option because disk layout v2 and below has no miniOS.

## How To Do Badapple
* Enter developer mode with ESC+REFRESH+POWER and CTRL+D
* When you reach dev mode block screen, press ESC+REFRESH+POWER again
* Select internet recovery
* when miniOS loads in, press CTRL+ALT+F3 (to open the VT3)
* You now have a shell you can type commands in

## Why Does This Stupid Exploit Work?

Because when you enter developer mode, cros_debug is flipped to 1 in crossystem's logic \
now the devs forgot that the recovery initramfs should always be trusted, whether in developer mode or not \
so they just put code in miniOS where if cros_debug == 1, open a shell in the VT3 \
because of googles oversight, we have a shell in the VT3 whilst enrolled. \
<https://source.chromium.org/chromiumos/chromiumos/codesearch/+/main:src/platform2/minios/ramfs/etc/init/debug-tty.conf;drc=a344af8a24700b3395cbaec1ab9b914f5b3d5b85;l=18>

# Exploit Support
:white_check_mark: icarus https://github.com/applefritter-inc/BadApple-icarus (uses updated certs generated by kxtz, cosmic and fanq) \
:x: cryptosmite(TBC)
