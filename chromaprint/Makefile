# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2026 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=chromaprint
PKG_VERSION:=1.6.0
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=v$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/acoustid/chromaprint
PKG_MIRROR_HASH:=9609cd52a01dd281f57211c791bb336f1926d831c4ed83aade27d96b242c4899

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=LGPL-2.1-only MIT
PKG_LICENSE_FILES:=LICENSE.md

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/chromaprint
  SECTION:=libs
  CATEGORY:=Libraries
  SUBMENU:=Sound
  TITLE:=audio fingerprint library
  URL:=https://github.com/acoustid/chromaprint
  DEPENDS:=+libffmpeg-full +libstdcpp
endef

define Package/chromaprint/description
 Chromaprint is an audio fingerprint library developed for the AcoustID project.
 It's designed to identify near-identical audio and the fingerprints it
 generates are as compact as possible to achieve that.
endef

CMAKE_OPTIONS += \
	-DBUILD_TOOLS=ON \
	-DBUILD_TESTS=OFF

TARGET_CXXFLAGS += -fpermissive

define Package/chromaprint/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/fpcalc $(1)/opt/bin
	$(INSTALL_DIR) $(1)/opt/lib
	$(CP) $(PKG_INSTALL_DIR)/opt/lib/libchromaprint.so.* $(1)/opt/lib
endef

$(eval $(call BuildPackage,chromaprint))
