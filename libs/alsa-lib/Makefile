#
# Copyright (C) 2006-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=alsa-lib
PKG_VERSION:=1.1.0
PKG_REV:=a748e4016db83262ce17fbfea26fed3b853f28bd
PKG_RELEASE:=2

PKG_SOURCE_URL:=git://github.com/tiwai/salsa-lib.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/alsa-lib
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=SALSA (Advanced Linux Sound Architecture) library
  URL:=http://www.alsa-project.org/main/index.php/SALSA-Library
endef

define Package/alsa-lib/description
  SALSA-Lib is a small, light-weight, hot and spicy version of
  the ALSA library, mainly for embedded systems with limited
  resources. The library is designed to be source-level compatible
  with ALSA library API for limited contents.
endef

CONFIGURE_ARGS += \
	--disable-deprecated \
	--enable-libasound \
	--enable-async \
	--enable-chmap \
	--enable-conf \
	--enable-timer \
	--enable-hwdep \
	--enable-output-buffer \
	--enable-seq \
	--enable-rawmidi \
	--enable-hwdep \
	--enable-tlv \
	--enable-ctlasciiparser \
	--enable-abicheck \
	--enable-conf

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/alsa
	$(CP) \
		$(PKG_BUILD_DIR)/src/*.h \
		$(1)/usr/include/alsa/

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/lib*.{la,so*} \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/alsa.pc \
		$(1)/usr/lib/pkgconfig/

	$(INSTALL_DIR) $(1)/usr/share/aclocal
	$(INSTALL_DATA) \
		$(PKG_BUILD_DIR)/alsa.m4 \
		$(1)/usr/share/aclocal/
endef

define Package/alsa-lib/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/lib*.so* \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,alsa-lib))
