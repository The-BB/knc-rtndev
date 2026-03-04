# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2025 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=rcon
PKG_VERSION:=0.6
PKG_RELEASE:=2

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/n0la/rcon
PKG_MIRROR_HASH:=37a9b19d2bbd223a9a1d80108f1f88651a504c77102548af390cadb7824ecf23

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=BSD-2-Clause
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk
include $(INCLUDE_DIR)/nls.mk

define Package/rcon
  SECTION:=games
  CATEGORY:=Games
  TITLE:=source RCON client
  URL:=https://github.com/n0la/rcon
  DEPENDS:=+glib2
endef

define Package/rcon/description
 Rcon is a command line application that can be used as a Source RCON client.
 It will send commands to the given server, and print the reply to stdout.
endef

define Package/rcon/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/rcon $(1)/opt/bin
endef

$(eval $(call BuildPackage,rcon))
