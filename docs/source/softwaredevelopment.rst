********************
Software Development
********************

===============================
1. Where do you get the toolchain?
===============================

byteDEVKIT
----------

* Yocto 3.0 MISSING Data

* Yocto 2.7 MISSING Data


bytePANEL
---------

* Yocto 3.0
  Download LINK: https://bytesatwork.ch/downloads/transfer/bytesatwork/poky-bytesatwork-glibc-x86_64-devbase-image-bytesatwork-armv7at2hf-neon-bytepanel-toolchain-3.0.1.sh

* Yocto 2.7
  Download LINK: https://bytesatwork.ch/downloads/transfer/bytesatwork/poky-bytesatwork-glibc-x86_64-devbase-image-bytesatwork-armv7at2hf-neon-bytepanel-toolchain-2.7.3.sh

============================================
2. Where do you get the Image for your SD-Card?
============================================

byteDEVKIT
----------

* Yocto 3.0 MISSING Data

* Yocto 2.7 MISSING Data

bytePANEL
---------

* Yocto 3.0
  Download LINK: https://bytesatwork.ch/downloads/transfer/bytesatwork/devbase-image-bytesatwork-bytepanel.wic.gz

* Yocto 2.7
  Downlad LINK: https://bytesatwork.ch/downloads/transfer/bytesatwork/m2/2.7/devbase-image-bytesatwork-bytepanel-emmc-20190729194430.sdimg.gz

============================================
3. How do you flash the Image?
============================================

byteDEVKIT
----------

* Yocto 3.0 MISSING Data

* Yocto 2.7 MISSING Data

bytePANEL
---------

* Yocto 3.0 MISSING Data

* Yocto 2.7 MISSING Data

============================================
4. How do you build an image?
============================================

byteDEVKIT
----------

* Yocto 3.0 & Yocto 2.7
   
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
	

bytePANEL
---------

* Yocto 3.0 MISSING Data

* Yocto 2.7 MISSING Data
