# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2025 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=encfs
PKG_VERSION:=1.9.5
PKG_RELEASE:=2

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=v$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/vgough/encfs
PKG_MIRROR_HASH:=3bcd422c96dd289c339c529e438854559df9d21a45b16f030ed33b987e0ba98e

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=GPL-3.0-or-later LGPL-3.0-or-later MIT
PKG_LICENSE_FILES:=COPYING COPYING.GPL COPYING.LGPL

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk
include $(INCLUDE_DIR)/nls.mk

define Package/encfs
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=Filesystem
  TITLE:=encrypted filesystem in user-space
  URL:=http://www.arg0.net/#!encfs/c1awt
  DEPENDS:=+fuse-utils +libatomic +libopenssl +libstdcpp $(ICONV_DEPENDS) $(INTL_DEPENDS)
endef

define Package/encfs/description
 EncFS provides an encrypted filesystem in user-space. It runs without any
 special permissions and uses the FUSE library module to provide the filesystem
 interface.
endef

CMAKE_OPTIONS += \
	-DBUILD_UNIT_TESTS=OFF

TARGET_LDFLAGS += -lpthread -latomic -lintl

define Package/encfs/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/encfs.bin $(1)/opt/bin/encfs
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/encfs{sh,ctl} $(1)/opt/bin
endef

$(eval $(call BuildPackage,encfs))
