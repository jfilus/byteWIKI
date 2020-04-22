********************
Software Development
********************

===============================
1. Where do you get the toolchain?
===============================

1.1 byteDEVKIT
----------

-  **Yocto 3.0 MISSING Data**


-  **Yocto 2.7 MISSING Data**


1.2 bytePANEL
---------

-  **Yocto 3.0**
  Download LINK: https://bytesatwork.ch/downloads/transfer/bytesatwork/poky-bytesatwork-glibc-x86_64-devbase-image-bytesatwork-armv7at2hf-neon-bytepanel-toolchain-3.0.1.sh
  

-  **Yocto 2.7**
  Download LINK: https://bytesatwork.ch/downloads/transfer/bytesatwork/poky-bytesatwork-glibc-x86_64-devbase-image-bytesatwork-armv7at2hf-neon-bytepanel-toolchain-2.7.3.sh

============================================
2. Where do you get the Image for your SD-Card?
============================================

2.1 byteDEVKIT
----------

-  **Yocto 3.0 MISSING Data**


-  **Yocto 2.7 MISSING Data**

2.2 bytePANEL
---------

-  **Yocto 3.0**
  Download LINK: https://bytesatwork.ch/downloads/transfer/bytesatwork/devbase-image-bytesatwork-bytepanel.wic.gz
  

-  **Yocto 2.7**
  Downlad LINK: https://bytesatwork.ch/downloads/transfer/bytesatwork/m2/2.7/devbase-image-bytesatwork-bytepanel-emmc-20190729194430.sdimg.gz

============================================
3. How do you flash the Image?
============================================

3.1 byteDEVKIT
----------

-  **Yocto 3.0 MISSING Data**


-  **Yocto 2.7 MISSING Data**

3.2 bytePANEL
---------

-  **Yocto 3.0 MISSING Data**


-  **Yocto 2.7 MISSING Data**

============================================
4. How do you build an image?
============================================

4.1 byteDEVKIT
----------

-  **Yocto 2.7 & Yocto 3.0**

   Use repo to download all necessary repositories:

   ::

      repo init -u https://github.com/bytesatwork/bsp-platform-st.git -b warrior repo sync

   If those commands are completed successfully, the following command
   will setup a Yocto Project environment for byteDEVKIT:

   ::

      MACHINE=bytedevkit DISTRO=poky-bytesatwork EULA=1 . setup-environment build

   The final command builds the development image:

   ::

      bitbake devbase-image-bytesatwork

   The output is found in:

   ::

      tmp/deploy/images/bytedevkit
	

4.2 bytePANEL
---------

-  **Yocto 2.7 & Yocto 3.0**

   Use repo to download all necessary repositories:

   ::

      repo init -u https://github.com/bytesatwork/bsp-platform.git -b zeus repo sync

   If those commands are completed successfully, the following command
   will setup a Yocto Project environment for bytePANEL:

   ::

      MACHINE=bytepanel DISTRO=poky-bytesatwork EULA=1 . setup-environment build

   the final command builds the development image:

   ::

      bitbake devbase-image-bytesatwork

   The output is found in:

   ::

      tmp/deploy/images/bytepanel
      
      
============================================
5. How do you build a toolchain?
============================================

5.1 byteDEVKIT
----------
-  **Yocto 2.7**

   ::

      repo init -u https://github.com/bytesatwork/bsp-platform-st.git -b warrior repo sync

   If those commands are completed successfully, the following command
   will setup a Yocto Project environment for byteDEVKIT:

   ::

      MACHINE=bytedevkit DISTRO=poky-bytesatwork EULA=1 . setup-environment build

   The final command builds an installable toolchain:

   ::

      bitbake devbase-image-bytesatwork -c populate_sdkbytePANEL

-  **Yocto 3.0**

   ::

      repo init -u https://github.com/bytesatwork/bsp-platform.git -b zeus repo sync

   If those commands are completed successfully, the following command
   will setup a Yocto Project environment for bytePANEL:

   ::

      MACHINE=bytepanel DISTRO=poky-bytesatwork EULA=1 . setup-environment build

   The final command builds an installable toolchain:

   ::

      itbake devbase-image-bytesatwork -c populate_sdk
      
============================================
6. How do you install the toolchain?
============================================

6.1 byteENGINE AM335x
----------

Download the Toolchain and install it
   ::

      sudo ./poky-bytesatwork-glibc-x86_64-devbase-image-bytesatwork-armv7at2hf-neon-bytepanel-toolchain-3.0.1.sh

6.2 byteENGINE STM32MP1x
----------

Download the Toolchain and install it
   ::

      sudo ./poky-bytesatwork-glibc-x86_64-devbase-image-bytesatwork-cortexa7t2hf-neon-vfpv4-bytedevkit-toolchain-2.7.2.sh
      
============================================
7. How do you use the toolchain?
============================================

7.1 byteENGINE AM335x
----------
Source the Toolchain

::

   source /opt/poky-bytesatwork/3.0.1/environment-setup-armv7at2hf-neon-poky-linux-gnueabi

Check if Cross-compiler is available in environment:

::

   echo $CC

::

   arm-poky-linux-gnueabi-gcc -march=armv7-a -mthumb -mfpu=neon -mfloat-abi=hard

::

   --sysroot=/opt/poky-bytesatwork/3.0.1/sysroots/armv7at2hf-neon-poky-linux-gnueabi

Crosscompile the source code, e.g. by:

::

   $CC helloworld.c -o helloworld

Check generated binary:

::

   file helloworld

::

   helloworld: ELF 32-bit LSB pie executable, ARM, EABI5 version 1
   
7.2 byteENGINE STM32MP1x
----------

Source the installed Toolchain:

::

   source /opt/poky-bytesatwork/2.7.2/environment-setup-cortexa7t2hf-neon-vfpv4-poky-linux-gnueabi

Check if Cross-compiler is available in environment:

::

   echo $CC

::

   arm-poky-linux-gnueabi-gcc -mthumb -mfpu=neon-vfpv4 -mfloat-abi=hard

::

   -mcpu=cortex-a7

::

   --sysroot=/opt/poky-bytesatwork/2.7.2/sysroots/cortexa7t2hf-neon-vfpv4-poky-linux-gnueabi

Crosscompile the source code, e.g. by:

::

   $CC helloworld.c -o helloworld

Check generated binary:

::

   file helloworld

::

   helloworld: ELF 32-bit LSB pie executable, ARM, EABI5 version 1

::
