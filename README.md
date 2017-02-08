# Enable kernel options for Docker

Add a simple option for enabling all the requirements for Docker to run.

## Install

1. Create a folder inside your kernel source tree, for example `utils`, then
place the Kconfig in there.
2. Add a line into the root Kconfig: `source "utils/Kconfig"`.

Sample final Kconfig:

    #
    # For a description of the syntax of this configuration file,
    # see Documentation/kbuild/kconfig-language.txt.
    #
    mainmenu "Linux/$ARCH $KERNELVERSION Kernel Configuration"

    config SRCARCH
            string
            option env="SRCARCH"

    source "utils/Kconfig"

    source "arch/$SRCARCH/Kconfig"


Now enable the Docker support option:

    Utilities --->
      [*] Docker support

And you should be good to go. Compile the kernel, install, reboot, enjoy.

## Credits

List created using information from the [Gentoo Docker Project](https://wiki.gentoo.org/wiki/Docker).
