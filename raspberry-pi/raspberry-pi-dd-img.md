#This is a How To use dd to copy a .img file to a SD Card

First you will need to download the img file of your choice

*   [www.raspberrypi.org](http://www.raspberrypi.org/downloads)
*   unzip the file you just downloaded
*   in cert you SD card into your computer. make sure you do not mount it and if it auto mounts, unmount it
*   sudo dd bs=4M if=/path/to/file.img of=/dev/mmcblk0

>Note:Make sure you get the right drive because you will over write the drive completely

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.