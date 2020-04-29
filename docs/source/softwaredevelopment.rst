********************
Software Development
********************
The entire development lifecycle is done in-house with transparent project management and customer involvement. We have proven experience in a wide range of industries, including industrial automation and custom solutions for consumer electronics. This section helps you step by step initiating the software development process: 

===============================
1. Where do you get the toolchain?
===============================

1.1 byteDEVKIT
----------

-  **Yocto 3.0**
  Download LINK: https://download.bytesatwork.io/transfer/bytesatwork/m5/3.0/poky-bytesatwork-glibc-x86_64-devbase-image-bytesatwork-cortexa7t2hf-neon-vfpv4-bytedevkit-toolchain-3.0.2.sh


-  **Yocto 2.7**
  Download LINK: https://download.bytesatwork.io/transfer/bytesatwork/poky-bytesatwork-glibc-x86_64-devbase-image-bytesatwork-cortexa7t2hf-neon-vfpv4-bytedevkit-toolchain-2.7.1.sh

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

-  **Yocto 3.0**
  Download LINK: https://download.bytesatwork.io/transfer/bytesatwork/m5/3.0/bytesatwork-minimal-image-bytedevkit.wic.gz 

-  **Yocto 2.7**
  Download LINK: https://download.bytesatwork.io/transfer/bytesatwork/m5/2.7/flashlayout_bytesatwork-minimal-image_FlashLayout_sdcard_stm32mp157c-bytedevkit.raw.gz


2.2 bytePANEL
---------

-  **Yocto 3.0**
  Download LINK: https://download.bytesatwork.io/transfer/bytesatwork/m2/3.0/bytesatwork-minimal-image-bytepanel-emmc-20200324165059.rootfs.wic.gz
  

-  **Yocto 2.7**
  Downlad LINK: https://bytesatwork.ch/downloads/transfer/bytesatwork/m2/2.7/devbase-image-bytesatwork-bytepanel-emmc-20190729194430.sdimg.gz

============================================
3. How do you flash the Image?
============================================

3.1 byteDEVKIT
----------

-  **Yocto 3.0**


   WINDOWS:

   ::

      Unzip the <file.wic.gz> (e.g. with 7-zip)
      Write the resulting <file.wic> to the uSD-card with a tool like Roadkil's Disk Image[https://www.roadkil.net/program.php?ProgramID=12]

   
   LINUX:

   ::

     gunzip -c <file.wic.gz> | dd of=/dev/mmcblk0 bs=8M conv=fdatasync status=progress
     To improve write performance, you could use bmap-tools: bmaptool copy <file.wic.gz> /dev/mmcblk0

-  **Yocto 2.7**

   WINDOWS:
   
   ::
   
     Unzip the <file.raw.gz> (e.g. with 7-zip)
     Write the resulting <file.raw> to the uSD-card with a tool like Roadkils Disk Image: https://www.roadkil.net/program.php?ProgramID=12

   LINUX:
   
   ::
   
     gunzip -c <file.raw.gz> | dd of=/dev/mmcblk0 bs=8M conv=fdatasync status=progress
     To improve write performance, you could use bmap-tools: bmaptool copy <file.raw.gz> /dev/mmcblk0

3.2 bytePANEL
---------

-  **Yocto 3.0**

   WINDOWS:
     
   ::
     
     Unzip the <file.wic.gz> (e.g. with 7-zip)
     Write the resulting <file.wic> to the uSD-card with a tool like Roadkils Disk Image: https://www.roadkil.net/program.php?ProgramID=12


  LINUX:
  
  ::
  
     gunzip -c <file.wic.gz> | dd of=/dev/mmcblk0 bs=8M conv=fdatasync status=progress
  
  
.. Hint:: To improve write performance, you could use bmap-tools: bmaptool copy <file.wic.gz> /dev/mmcblk0

-  **Yocto 2.7**

  WINDOWS:
  
  ::
  
     Unzip the <file.sdimg.gz> (e.g. with 7-zip)
     Write the resulting <file.sdimg> to the uSD-card with a tool like Roadkils Disk Image[https://www.roadkil.net/program.php?ProgramID=12]

  LINUX:
  
  ::
  
     gunzip -c <file.sdimg.gz> | dd of=/dev/mmcblk0 bs=8M conv=fdatasync status=progress

  
  
.. Hint:: To improve write performance, you could use bmap-tools: bmaptool copy <file.sdimg.gz> /dev/mmcblk0

============================================
4. How do you build an image?
============================================

4.1 byteDEVKIT
----------

-  **Yocto 2.7 & Yocto 3.0**

   Use repo to download all necessary repositories:

   ::

      repo init -u https://github.com/bytesatwork/bsp-platform-st.git -b warrior
      repo sync

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

      repo init -u https://github.com/bytesatwork/bsp-platform.git -b zeus
      repo sync

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
      
      
4.3 How to modify the image
---------

-  **bytesatwork delivers tips for customizing an image**

The image recipes can be found in

  ::

     sources/meta-bytesatwork/recipes-core/images.
     
This is relative to where you started you repo command to check out all the sources.

Edit the minimal-image recipe:

  ::

     bytesatwork-minimal-image.bb 

Add the desired software-package to IMAGE_INSTALL variable, for example:

   ::

     add net-tools to bytesatwork-minimal-image.bb

Rebuild the image.

4.4 How to rename the image
---------

-  **If you want to rename or copy an image, simple rename or copy the image recipe, e.g. by:**

  ::
  
     cp bytesatwork-minimal-image.bb customer-example-image.bb


4.5 Troubleshooting
---------

-  **Image size is to small:**

   If you encounter that your image size is to small to install additional software, 
   please have a look at the :guilabel:`IMAGE_ROOTFS_SIZE` variable under 
   :guilabel:`meta-bytesatwork/recipes-core/images/bytesatwork-minimal-image.bb`

-  Increase the size if necessary.

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

Cross-compile the source code, e.g. by:

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


============================================
8. How to bring your binary to the target?
============================================

1. Connect the embedded device's ethernet to your LAN
2. Run: :guilabel:`dhclient` on the embedded target
3. determine the embedded target ip address by :guilabel:`ip addr show`
4. scp your binary, e.g. hello world to the target by :guilabel:`scp helloworld root@<ip address of target>:/tmp`
    
============================================
9. How to install additional software using apt
============================================

1. Connect the embedded device's ethernet to your LAN
2. Run: :guilabel:`dhclient` on the embedded target
3. Run: :guilabel:`apt-get update`
4. Run: :guilabel:`apt-get install <software component>` to install additional software
   e.g.: :guilabel:`apt-get install openssh-sshd openssh-scp`
