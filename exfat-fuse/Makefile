# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2025 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=exfat-fuse
PKG_VERSION:=1.4.0
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=v$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/relan/exfat
PKG_MIRROR_HASH:=9b593b947096ca4365826f398606da532c88098668fe66814de1d15829d97241

PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING
PKG_MAINTAINER:=Entware team, https://entware.net

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/exfat-fuse
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=Filesystem
  TITLE:=Utilities for exFAT file system
  URL:=https://github.com/relan/exfat
  DEPENDS:=+fuse3-utils
endef

define Package/exfat-fuse/description
 This project aims to provide a full-featured exFAT file system implementation
 for Unix-like systems. It consists of a FUSE module (fuse-exfat) and a set of
 utilities (exfat-utils).
endef

define Package/exfat-fuse/install
	$(INSTALL_DIR) $(1)/opt/sbin
	$(CP) $(PKG_INSTALL_DIR)/opt/sbin/* $(1)/opt/sbin
endef

$(eval $(call BuildPackage,exfat-fuse))
