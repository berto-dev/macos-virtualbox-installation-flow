


![MacOsVbox](./resources/banner.png)

------



## MAC OS (BIG SUR) VIRTUALIZED - CUSTOM START PIPELINE

A pipelines it's a simple step by step roles for make somethings better.
This file is a simple annotations for custom installation of virtualbox and basic environment for  *virtual machine + Mac Os Big Sur + extras*.

Important note: **it's under costruction and based on personal use.** 



------



## Installation:

> Although it's only for compiling, I would recommend an hackintosh on a dedicated partition due the poor performance of vm. However...


 - get and use the [VirtualBox installer](https://www.virtualbox.org/wiki/Downloads) and the [extension pack](https://download.virtualbox.org/virtualbox/6.1.30/Oracle_VM_VirtualBox_Extension_Pack-6.1.30.vbox-extpack)<br>
 
 - download [direct big sur 11.X](https://www.mediafire.com/file/9vuo3rcmv0r8ag4/MAC_OS_BIG_SUR.rar/file) (warning: all image have a specific code)<br>
   
 - Before installation, unlock [Intel VT-x or AM VT-x (virtualization technology) in bios](https://www.google.com/search?q=enable+virtualization+technology+in+bios&sxsrf=AOaemvJqJGxSXODQZwQzVTrWEPeETGHFZQ%3A1639660921382&source=hp&ei=eT27Yd-BFcyWa5mKh8AD&iflsig=ALs-wAMAAAAAYbtLid-l_YeXm7_G93bWOGP2k6Pm2f1F&oq=unlock+virtualization+tec&gs_lcp=Cgdnd3Mtd2l6EAMYATIGCAAQFhAeMgYIABAWEB4yBggAEBYQHjIGCAAQFhAeMggIABAWEAoQHjIGCAAQFhAeMgYIABAWEB4yBggAEBYQHjIGCAAQFhAeMgYIABAWEB46BAgjECc6EQguEIAEELEDEIMBEMcBEKMCOg4ILhCABBCxAxDHARCjAjoLCC4QgAQQsQMQgwE6CgguEMcBENEDEEM6CwgAEIAEELEDEIMBOggIABCxAxCDAToECC4QQzoECAAQQzoHCAAQsQMQQzoFCAAQgAQ6CAgAEIAEELEDOgUILhCABDoECAAQEzoGCAAQChATOggIABAWEB4QEzoKCAAQFhAKEB4QEzoFCCEQoAE6BAghEBVQAFjWP2DWTmgBcAB4AIABoQGIAZwSkgEEMTQuOZgBAKABAQ&sclient=gws-wiz).<br>
   After VirtualBox installation:<br>
   
   - open vb > preference > change default vm folder in (suggest name) C:/Virtualized<br>
     _or other simpled folder for check contents of vm_
   
   - make new vm and:<br>
     **warning: if not follow it litterally, you do a _*starterror_**
   
     - named it Big Sur, <br>
       select folder Big Sur,<br>
       select Mac OS X, Mac OS X (64-bit)<br>set 4096 | 8192 | 16384 | 32768 of ram,<br>set dynamic VDI,<br>
       min 60gb SSD,<br>
       
       <br>in system set:  VCH9 (in same case PIIX3 is better)<br>in system set: remove floppy<br>
       in system set:  4 | 6 | 8  CPU<br>in system set: standard VBoxSVGA 128Mb | 256Mb (no accelleration)<br>in system, accelleration:<br>
           for intel cpu set minimal<br>    for AMD cpu set minimal (not tested) and read after for starterror<br>in usb set: USB 3.0<br>in archive set: sata1 is SSD;<br>
       
       <br>
       
       in general set: _bidirectional_ and _bidirectional_<br><br>
       
     - Close VM, open prompt in admin...:<br>
       Copy and past inside terminal <br>
     
       ```
       cd "C:\Program Files\VirtualBox\"
       ```
       
       or other installation of vitualbox forlder ( for me: `cd "C:\Program Files\VirtualBox\"`) <br>
       
       and:<br>
       
       ```
       VBoxManage.exe modifyvm "Big Sur" --cpuidset 00000001 000106e5 00100800 0098e3fd bfebfbff
       VBoxManage setextradata "Big Sur" "VBoxInternal/Devices/efi/0/Config/DmiSystemProduct" "iMac11,3"
       VBoxManage setextradata "Big Sur" "VBoxInternal/Devices/efi/0/Config/DmiSystemVersion" "1.0"
       VBoxManage setextradata "Big Sur" "VBoxInternal/Devices/efi/0/Config/DmiBoardProduct" "Iloveapple"
       VBoxManage setextradata "Big Sur" "VBoxInternal/Devices/smc/0/Config/DeviceKey" "ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc"
       VBoxManage setextradata "Big Sur" "VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" 1
       
       ```
       
       extra:<br>
       
       ```
       VBoxManage setextradata "Big Sur" vBoxItenal2/EfiGraphicsResoltion 1024x768
       
       or...
       1280x720 | 1920x1080 | 2560x1440 | 2048x1080 | 3840x2160 | 5120x2880 | 1280x800 | 1280x1024 |1600x900 | 1440x900
       ```
       
       <br>-_-_-_-_-<br>
       the **starteerror** and how fix it: <br>
       "LOG: EXITBS :START" has a infinite waiting problem of hackintosh during installation in vm. For Intel resolve it with a precised start configuration (see below instruction). In AMD, you can try extra solutions  because -probably- is relative to a wrong "intel cpu profile"... Add ONE of this lines in promp (equal to up) :
       
       ```
       VBoxManage modifyvm "Big Sur" --cpu-profile "Intel Core i7-6700K" <= standard
       VBoxManage modifyvm "Big Sur" --cpu-profile "Intel Core i7-5600U"
       VBoxManage modifyvm "Big Sur" --cpu-profile "Intel Core i7-3960X"
       VBoxManage modifyvm "Big Sur" --cpu-profile "Intel Core i7-2635QM"
       VBoxManage modifyvm "Big Sur" --cpu-profile "Intel Core i5-3570"
       VBoxManage modifyvm “Big Sur” –cpu-profile “Intel Xeon X5482 3.20GHz”
       ```
       
       In other case program crash beacouse big sur image is broken... you can't do anything, change image online and update the terminal codes.<br>-_-_-_-_-<br>
       
     - Close terminal, reopen and start the VM<br>
       
       ... system load mac image for install it (wait end of load... it's slow).<br>
       if it not start, on end of load write "exit" and go on boot loader and start with "boot from cd-rom"<br>
       <br>
     
   - MacOS installation :<br>
   
     - select English<br>
     - open utility disk  VBOX HARDDISK Media and erese/initalized it with name "Big Sur"<br>
     - close utility and install the OS<br>_WARNING: wait more, be patient, I'ts really... really slow._<br>
     - reopen settings of VM and powered it<br>


<!-- video istruction [virtualization of Mac OS](https://www.youtube.com/watch?v=0RJWGWQfgYs)-->
