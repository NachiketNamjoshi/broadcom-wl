# broadcom-wl
After getting pissed by broadcom providing unfinished drivers and modules, I decided to finish their job.

# Project Notes:
1. 26/7/16 : Initial Workaround
2. 27/7/16 : Sorted/Figured out which headers are used by whom.
  * src/common - used by BCM4311-, BCM4312-, BCM4313-, BCM4321-, BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228
  * src/shared - still not sure, but overall everyone uses some of the headers there.
  * src/include - as far as I am concerned, BCM4312 specifically uses this.			
3. 29/7/16 : Pulled the structs to a single file and implemented new names for the structs, Updated README.md

# Installation

Use following commands to build (Will provide a build script for relatively new users
once it is complete)
----------------------------------------------------------------------------------------------------------------------------
#### NOTE: Execute all as root

* `cd /path/to/hybrid-wl/folder`
* `make`
* `make install`
* `modprobe -r bcma`
* `echo "blacklist bcma" > /etc/modprobe.d/broadcom.conf`
* `echo "wl" > /etc/modules-load.d/wl.conf`
* `depmod -a`
* `modprobe wl`

--------------------------------------------------------------------------------------------------------------------------
## Sources:
* http://www.broadcom.com/support/802.11/linux_sta.php

