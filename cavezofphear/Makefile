# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2026 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=cavezofphear
PKG_VERSION:=0.6.2
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=83a43ab7d5aa597f24d18bd0c282b409bed3395f
PKG_SOURCE_URL:=https://github.com/AMDmi3/cavezofphear
PKG_MIRROR_HASH:=e6f73723bf54f44d6e666c3b64c4b593616844540bfaf64991a8dbe654b6aeb9

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=GPL-3.0-or-later
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/cavezofphear
  SECTION:=games
  CATEGORY:=Games
  TITLE:=CAVEZ of PHEAR is a boulder dash / digger like game
  URL:=$(PKG_SOURCE_URL)
  DEPENDS:=+libncurses
endef

define Package/cavezofphear/description
 CAVEZ of PHEAR is a boulder dash / digger like game for console / terminals
 using ncurses. The goal of this game is to escape through the caves by
 collecting diamonds and avoid falling stones.
endef

CMAKE_OPTIONS += \
	-DWITH_MANPAGE=OFF \
	-DSYSTEMWIDE=ON

define Package/cavezofphear/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/phear $(1)/opt/bin
	$(INSTALL_DIR) $(1)/opt/share
	$(CP) $(PKG_INSTALL_DIR)/opt/share/phear $(1)/opt/share
endef

$(eval $(call BuildPackage,cavezofphear))
