# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2025 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=castget
PKG_VERSION:=2.0.1
PKG_RELEASE:=3

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=rel_$(subst .,_,$(PKG_VERSION))
PKG_SOURCE_URL:=https://github.com/mlj/castget
PKG_MIRROR_HASH:=ea72263c0705d1367743444727e34d9fae06abb6732b01c9ba4fd3673fdf486b

PKG_LICENSE:=GPL-2.0-or-later LGPL-2.1-or-later
PKG_LICENSE_FILES:=COPYING COPYING.LIB
PKG_MAINTAINER:=Entware team, https://entware.net

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk

define Package/castget
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=File Transfer
  TITLE:=a command-line podcast downloader
  URL:=https://castget.johndal.com/
  DEPENDS:=+glib2 +id3lib +libcurl +libxml2 +libstdcpp $(ICONV_DEPENDS) $(INTL_DEPENDS)
endef

define Package/castget/description
 castget is a simple, command-line based RSS enclosure downloader.
 It is primarily intended for automatic, unattended downloading of podcasts.
endef

define Package/castget/conffiles
/opt/etc/castgetrc
endef

define Package/castget/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/castget $(1)/opt/bin
	$(INSTALL_DIR) $(1)/opt/etc
	$(INSTALL_CONF) $(PKG_BUILD_DIR)/castgetrc.example $(1)/opt/etc/castgetrc
endef

$(eval $(call BuildPackage,castget))
