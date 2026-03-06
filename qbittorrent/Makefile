# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2017-2026 Entware

# ported to Entware from https://github.com/KryptonLee/qBittorrent-openwrt-package

include $(TOPDIR)/rules.mk

PKG_NAME:=qbittorrent
PKG_VERSION:=5.1.4
PKG_RELEASE=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=release-$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/qbittorrent/qbittorrent
PKG_MIRROR_HASH:=588ceb3a581916b1e24443db8d7ec7a8561466fb7643a03908074da028f63aca

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=GPL-2.0-or-later GPL-3.0-or-later
PKG_LICENSE_FILES:=COPYING COPYING.GPLv2 COPYING.GPLv3

PKG_BUILD_DEPENDS:=qt6base qt6tools/host
PKG_BUILD_FLAGS:=no-mips16

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/qbittorrent
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=BitTorrent
  TITLE:=a BitTorrent client in Qt
  URL:=https://www.qbittorrent.org/
  DEPENDS:=+libtorrent-rasterbar $(ICONV_DEPENDS) $(INTL_DEPENDS)
endef

define Package/qbittorrent/description
 qBittorrent is a bittorrent client programmed in C++ / Qt that uses
 libtorrent (sometimes called libtorrent-rasterbar) by Arvid Norberg.
 It aims to be a good alternative to all other bittorrent clients out
 there. qBittorrent is fast, stable and provides unicode support as
 well as many features.
endef

TARGET_CPPFLAGS:=$(filter-out -I%fortify,$(TARGET_CPPFLAGS))
TARGET_CXXFLAGS += -pthread
TARGET_LDFLAGS += -latomic -pthread

CMAKE_OPTIONS += \
	-DGUI=OFF \
	-DDBUS=OFF \
	-DSTACKTRACE=OFF

define Package/qbittorrent/install
	$(INSTALL_DIR) $(1)/opt/bin $(1)/opt/etc/init.d
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/qbittorrent-nox $(1)/opt/bin
	$(INSTALL_BIN) files/S89qbittorrent $(1)/opt/etc/init.d
endef

$(eval $(call BuildPackage,qbittorrent))
