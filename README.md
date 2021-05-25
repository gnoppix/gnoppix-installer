Gnoppix installer 

Introduction

Debian-installer (d-i) is the preferred way of installing debian based systems. It runs in the initrd/initramfs (see notes/DebianInstaller).

di-live's objective is to provide the ability to install a "live" debian based system direct to the harddisk, leveraging the power/flexability of d-i, with a completely modular implementation (least amount of assumptions) that can be used by upstream (eg. as an ubiquity depends - seperation of concerns).

Source structure

di-live.py - top level executable script (symlinked from bin/di-live) di-live - drives the installation (similar to d-i's main-menu) di-live.d/ - component directory (executed in alpha-numeric ordering) d-i/ - upstream d-i source code compat/ - compatibility scripts as d-i code assumes running in

initrd/initramfs
cli syntax

The init script will execute di-live using dialog frontend (unless -d|--debug is used) if the boot param "di-live" is present on /proc/cmdline. di-live may be executed manually in a live system as well.

Syntax: di-live [options]

Debian Installer Live

Drives the installation, executing components according to alpha-numeric ordering, and responsible for dynamically assembling the menu and executing components when they are selected.

Similar to d-i's main-menu, di-live's menu will only be visible when debconf priority is low or medium. Priority is reduced when a component fails, and returns to original level when next component completes successfully.

Options:
-d --debug Set DEBCONF_DEBUG=developer DEBIAN_FRONTEND=readline

