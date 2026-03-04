# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2022-2025 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=7-zip
PKG_VERSION:=25.01
PKG_RELEASE:=1

PKG_SOURCE:=7z$(subst .,,$(PKG_VERSION))-src.tar.xz
PKG_SOURCE_URL:=https://www.7-zip.org/a
PKG_HASH:=ed087f83ee789c1ea5f39c464c55a5c9d4008deb0efe900814f2df262b82c36e

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=LGPL-2.0-only

include $(INCLUDE_DIR)/package.mk

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) -xf $(DL_DIR)/$(PKG_SOURCE)

define Package/7-zip
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=Compression
  TITLE:=file archiver with a high compression ratio
  URL:=https://www.7-zip.org
  DEPENDS:=+libstdcpp
endef

define Package/7-zip/description
 File archiver with a high compression ratio.
endef

MAKE_PATH:=CPP/7zip/Bundles/Alone2

MAKE_VARS += \
	MY_ARCH="$(TARGET_CFLAGS) $(TARGET_LDFLAGS)"

define Build/Prepare
	$(PKG_UNPACK)
	chmod +w -R $(PKG_BUILD_DIR)/*
	$(Build/Patch)
endef

define Build/Compile
	$(call Build/Compile/Default,-f makefile.gcc)
endef

define Package/7-zip/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/$(MAKE_PATH)/_o/7zz $(1)/opt/bin
endef

$(eval $(call BuildPackage,7-zip))
