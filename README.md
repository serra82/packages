Openwrt packages for shairport (now also in openwrt trunk)
==================================================

add feed in feeds.conf:
	
	src-git serra82 git://github.com/serra82/packages.git;master

and patch

	cd ~/trunk/feeds/serra82
	wget -O - ...url.../shairport_deps_trunk.diff | patch -p1
	
or

	cat shairport_deps_trunk.diff | patch -p1
	
example of shairport_deps_trunk.diff:

	diff --git a/sound/shairport/Makefile b/sound/shairport/Makefile
	index c62ad91..e2a754b 100644
	--- a/sound/shairport/Makefile
	+++ b/sound/shairport/Makefile
	@@ -1,5 +1,5 @@
 	#
	-# Copyright (C) 2011 OpenWrt.org
	+# Copyright (C) 2012 OpenWrt.org
	 #
	 # This is free software, licensed under the GNU General Public License v2.
	 # See /LICENSE for more information.
	@@ -32,7 +32,7 @@ endef
	 
	 define Package/shairport
	   $(Package/shairport/Default)
	-  DEPENDS:= +libopenssl +libao +avahi-daemon-dbus +avahi-utils
	+  DEPENDS:= +libopenssl +libao +avahi-daemon +libavahi-dbus-support +avahi-utils
	 endef
	 
	 define Package/shairport/description


and now select shairport under make menuconfig->sound
