# 说明：
### 修改部分

1. 修改文件 EmuELEC/projects/Amlogic/filesystem/usr/sbin/installtointernal  
原版文件把EmuELEC写入到emmc中虽然可以，但是用户数据却没有，替换后可以完美写入emmc  
参考https://www.znds.com/tv-1152747-1-1.html

2. 修改配置文 EmuELEC/packages/sx05re/emuelec/config/emuelec/configs/emuelec.conf
默认开启WiFi
默认语言设置为中文
默认失去设置为Asia/Shanghai(中国上海)
Retroarch主题默认为xmb样式

3. 修改了Emulationstation编译文件 EmuELEC/packages/sx05re/emuelec-emulationstation/package.mk
地址改为Fork后自己修改后的项目地址 PKG_SITE="https://github.com/Ryukarin/batocera-emulationstation"
对部分没有汉化的内容进行补充汉化,待测试...
后续跟进...

4. 对系统版本文件的修改 EmuELEC/packages/sx05re/emuelec/config/EE_VERSION
修改后,版本为"3.8_Ryuukarin整合"
进入ES主菜单最下面会显示版本信息,或主菜单---系统设置---系统信息---版本


#编译:  
###环境：Ubuntu 20.04.1 LTS

```
sudo apt update && sudo apt upgrade
sudo apt-get install gcc make git unzip wget xz-utils libsdl2-dev libsdl2-mixer-dev libfreeimage-dev libfreetype6-dev libcurl4-openssl-dev rapidjson-dev libasound2-dev libgl1-mesa-dev build-essential libboost-all-dev cmake fonts-droid-fallback libvlc-dev libvlccore-dev vlc-bin texinfo premake4 golang libssl-dev curl patchelf xmlstarlet
git clone https://github.com/Ryukarin/EmuELEC.git EmuELEC    
cd EmuELEC  
git checkout master  
PROJECT=Amlogic ARCH=arm DISTRO=EmuELEC make image   
```
对于Odroid N2设备： 

`PROJECT=Amlogic-ng ARCH=arm DISTRO=EmuELEC make image`

如果要构建插件：
```
cd EmuELEC
./emuelec-addon.sh
```
生成的zip文件将位于EmuELEC/repo中

**请记住为您的设备使用正确的DTB！**


---

# EmuELEC  
Retro emulation for Amlogic devices.  
Based on  [CoreELEC](https://github.com/CoreELEC/CoreELEC) and [Lakka](https://github.com/libretro/Lakka-LibreELEC) with tidbits from [Batocera](https://github.com/batocera-linux/batocera.linux). I just combine them with [Batocera-Emulationstation](https://github.com/batocera-linux/batocera-emulationstation) and some standalone emulators ([Advancemame](https://github.com/amadvance/advancemame), [PPSSPP](https://github.com/hrydgard/ppsspp), [Reicast](https://github.com/reicast/reicast-emulator), [Amiberry](https://github.com/midwan/amiberry) and others). 

To build use:  

```
sudo apt update && sudo apt upgrade
sudo apt-get install gcc make git unzip wget xz-utils libsdl2-dev libsdl2-mixer-dev libfreeimage-dev libfreetype6-dev libcurl4-openssl-dev rapidjson-dev libasound2-dev libgl1-mesa-dev build-essential libboost-all-dev cmake fonts-droid-fallback libvlc-dev libvlccore-dev vlc-bin texinfo premake4 golang libssl-dev curl patchelf xmlstarlet
git clone https://github.com/shantigilbert/EmuELEC.git EmuELEC    
cd EmuELEC  
git checkout master  
PROJECT=Amlogic ARCH=arm DISTRO=EmuELEC make image   
```
For the Odroid N2:   
`PROJECT=Amlogic-ng ARCH=arm DISTRO=EmuELEC make image`

if you want to build the addon: 
```
cd EmuELEC
./emuelec-addon.sh
```
resulting zip files will be inside EmuELEC/repo

**Remember to use the proper DTB for your device!**


If you want to open a PR please do so on the dev branch :) 

Need help? have suggestions? check out the Wiki at https://github.com/EmuELEC/EmuELEC/wiki or join us on our EmuELEC Discord: https://discord.gg/cbgtJTu

**EmuELEC DOES NOT INCLUDE KODI**

Please note, this is mostly a personal project made for my S905 box I can't guarantee that it will work for your box, I've spent many hours trying to optimize and make sure everything works, but I can't test everything and things might just not work at all, also keep in mind the limitations of the hardware and don't expect everything to run at 60FPS (specially N64, PSP and Reicast) I can't guarantee changes to fit your personal needs, but I do appreciate any PRs, help on testing other boxes and fixing issues in general.  
I work on this project on my personal time, I don't make any money out of it, so it takes a while for me to properly test any changes, but I will do my best to help you fix issues you might have on other boxes limited to my time and experience. 

**License**

EmuELEC is based on CoreELEC which in turn is licensed under the GPLv2 (and GPLv2-or-later), all original files created by the EmuELEC team are licensed as GPLv2-or-later and marked as such.

However, the distro includes many non-commercial emulators/libraries/cores/binaries and as such, **it cannot be sold, bundled, offered, included, or anything similar, in any commercial product/application including but not limited to: Android Devices, Smart-TVs, TV-boxes, Hand-held Devices, Computers, SBCs, or anything else that can run EmuELEC.** with those emulators/libraries/cores/binaries included.

I will also add this from the CoreELEC readme, adapted to EmuELEC:

As EmuELEC includes code from many upstream projects it includes many copyright owners. EmuELEC makes NO claim of copyright on any upstream code. Patches to upstream code have the same license as the upstream project, unless specified otherwise. For a complete copyright list please checkout the source code to examine license headers. Unless expressly stated otherwise all code submitted to the EmuELEC project (in any form) is licensed under GPLv2-or-later. You are absolutely free to retain copyright. To retain copyright simply add a copyright header to each submitted code page. If you submit code that is not your own work it is your responsibility to place a header stating the copyright.

**Branding**

All EmuELEC related logos, videos, images and branding in general are the sole property of EmuELEC and they are all Copyrighted by the EmuELEC team and are not to be included in any commercial application whatsoever without the proper authorization, (yes, this includes EmuELEC bundled with ROMS for donations!).

You are however granted permission to include/modify them in your forks/projects as long as they are completely open-source, freely available (as in [but not limited to] not under a bunch of "click this sponsored ad to get the link!"), and do not infringe on any copyright laws, even if you receive donations for such project (we are not against donations for honest people!), we only ask that you give us the proper credit and if possible a link to this repo.

Happy retrogaming! 
