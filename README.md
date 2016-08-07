# broadcom-wl
After getting pissed by broadcom providing unfinished drivers and modules, I decided to finish their job.

# Project Notes:
1. 26/7/16 : Initial Workaround
2. 27/7/16 : Sorted/Figured out which headers are used by whom.
  * src/common - used by BCM4311-, BCM4312-, BCM4313-, BCM4321-, BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228
  * src/shared - still not sure, but overall everyone uses some of the headers there.
  * src/include - as far as I am concerned, BCM4312 specifically uses this.			
3. 29/7/16 : Pulled the structs to a single file and implemented new names for the structs, Updated README.md
4. 30/8/16 : Fix Broadcom blunder, they used eth instead of wlan for their "wireless driver"
5. 2/8/16 : After seeing and comparing their code switched to an earlier source
  * changed from `6.30.223.271` to `6.30.223.141`
  * fixed cfg80211: on compiling, it gave `E: Too Few Arguments`
    * since it was an older code, new linux headers weren't included
    * to be specific, headers from `linux 3.15.x` were missing
    * added conditional functions to map with the different function definitions
6. 4/8/16 : wl_linux: Added Monitor mode support. it does go to monitor mode
  * need testing on this one, and can still be marked under `WIP`
  * since our focus is to fix the driver from dropping connections randomly, I shall not concentrate on this feature for now
7. 6/8/16 : Update sources, pushed commits, update readme
  * side note:
    ```
    Use only 802.11b for better results for now, idk why but "b" is not dropping connections, I had a solid 12 hours of continuous idle connection and it didn't drop. 
    ```
 8. 7/8/16 : Update All Sources from `6.30.223.141` to `6.30.223.271`
   * Updated each and every file with changes that were done previously.
   * Adapted new naming from `wl` to `reacted_wl`
   * Updated `README.md`
 
###### As of now, Current Sources and my sources are parallel and work properly.
###### 802.11 b/g/n all of them working properly. I personally use 802.11g
###### And I do not face any problems (mostly).

# Installation

Use following commands to build (Will provide a build script for relatively new users
once it is complete)

#### NOTE: Execute all as root

* `cd /path/to/hybrid-wl/folder`
* `make`
* `make install`
* `modprobe -r bcma`
* `echo "blacklist bcma" > /etc/modprobe.d/broadcom.conf`
* `echo "reacted_wl" > /etc/modules-load.d/wl.conf`
* `depmod -a`
* `modprobe reacted_wl`

--------------------------------------------------------------------------------------------------------------------------
## Sources:
* http://www.broadcom.com/support/802.11/linux_sta.php

