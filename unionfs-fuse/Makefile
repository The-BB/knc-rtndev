# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2026 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=unionfs-fuse
PKG_VERSION:=3.7
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=v$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/rpodgorny/unionfs-fuse
PKG_MIRROR_HASH:=0ab353b59c90450341dd1111d92bb175368ce10ae1c3a122096da289bf963dc7

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/unionfs-fuse
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=Filesystem
  TITLE:=user-space implementation of union filesystem
  URL:=https://github.com/rpodgorny/unionfs-fuse
  DEPENDS:=+fuse3-utils
endef

define Package/unionfs-fuse/description
 unionfs filesystem implementation which is way more flexible than
 the current in-kernel unionfs solution.
endef

define Package/unionfs-fuse/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/unionfs{,ctl} $(1)/opt/bin
endef

$(eval $(call BuildPackage,unionfs-fuse))
