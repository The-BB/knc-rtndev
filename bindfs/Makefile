# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2026 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=bindfs
PKG_VERSION:=1.18.3
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://bindfs.org/downloads
PKG_HASH:=178a723d7039bae3ab1cef2fc93e5e8693c4184f52519c0e9a1deee93b838df1

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/bindfs
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=Filesystem
  TITLE:=a FUSE filesystem for mounting
  URL:=https://bindfs.org
  DEPENDS:=+fuse3-utils
endef

define Package/bindfs/description
 bindfs is a FUSE filesystem for mirroring a directory to
 another directory, similarly to mount --bind. The permissions of the
 mirrored directory can be altered in various ways.
endef

define Package/bindfs/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/bindfs $(1)/opt/bin
endef

$(eval $(call BuildPackage,bindfs))
