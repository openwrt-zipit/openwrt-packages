#
# Copyright (C) 2007-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=nano
PKG_VERSION:=2.7.0
PKG_RELEASE:=1
PKG_LICENSE:=GPL-3.0+
PKG_LICENSE_FILES:=COPYING

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=@GNU/nano
PKG_MD5SUM:=f86af39514ae74e20bef3c29cd01d1090a9aca772a70e9c9f9e70c3d14b39521

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/nano
  SUBMENU:=Editors
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=An enhanced clone of the Pico text editor
  URL:=http://www.nano-editor.org/
  MAINTAINER:=Jonathan Bennett <JBennett@incomsystems.biz>
  DEPENDS:=+libncurses
endef

define Package/nano/description
  Nano (Nano's ANOther editor, or Not ANOther editor) is an enhanced clone
  of the Pico text editor.
endef

define Package/nano-syntax
  $(call Package/nano/Default)
  SUBMENU:=Editors
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Syntax highlighting definitions for nano editor
  URL:=http://www.nano-editor.org/
  MAINTAINER:=Jonathan Bennett <JBennett@incomsystems.biz>
  DEPENDS:=+nano
endef

CONFIGURE_ARGS += \
	--disable-glibtest \
	--disable-utf8 \
	--disable-libmagic \
    --without-slang 

CONFIGURE_VARS += \
	ac_cv_header_regex_h=yes \

define Package/nano/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/$(PKG_NAME) $(1)/usr/bin/
endef

define Package/nano-syntax/install
	$(INSTALL_DIR) $(1)/etc
		$(CP) ./files/nanorc $(1)/etc/
	$(INSTALL_DIR) $(1)/usr/share/nano
		$(CP) ./files/makefile.nanorc $(1)/usr/share/nano/
		$(CP) ./files/nanorc.nanorc $(1)/usr/share/nano/
		$(CP) ./files/c.nanorc $(1)/usr/share/nano/
		$(CP) ./files/sh.nanorc $(1)/usr/share/nano/
		$(CP) ./files/patch.nanorc $(1)/usr/share/nano/
		$(CP) ./files/xml.nanorc $(1)/usr/share/nano/
		$(CP) ./files/js.nanorc $(1)/usr/share/nano/
endef

$(eval $(call BuildPackage,nano))
$(eval $(call BuildPackage,nano-syntax))