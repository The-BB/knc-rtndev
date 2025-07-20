# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2025 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=vitetris
PKG_VERSION:=0.59.1
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=v$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/vicgeralds/vitetris
PKG_MIRROR_HASH:=4b1768c31692420f63ac76509b02b5bcc1ed12a4dd5fb85752cf8491c237ebfb

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=BSD-2-Clause
PKG_LICENSE_FILES:=licence.txt

include $(INCLUDE_DIR)/package.mk

define Package/vitetris
  SECTION:=games
  CATEGORY:=Games
  TITLE:=Terminal-based Tetris clone
  URL:=http://www.victornils.net/tetris
  DEPENDS:=+libncurses
endef

define Package/vitetris/description
 Vitetris is a terminal-based Tetris clone by Victor Nilsson.
 Gameplay is much like the early Tetris games by Nintendo. Features include:
 configurable keys, highscore table, two-player mode with garbage, network play.
endef

define Build/Configure
	cd $(PKG_BUILD_DIR); \
	CC="$(TARGET_CC)" \
	CFLAGS="$(TARGET_CFLAGS)" \
	CPPFLAGS="$(TARGET_CPPFLAGS)" \
	LDFLAGS="$(TARGET_LDFLAGS)" \
	./configure \
		--prefix=$(PKG_INSTALL_DIR) \
		--without-joystick \
		--without-xlib \
		--with-curses
endef

define Package/vitetris/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/tetris $(1)/opt/bin/vitetris
endef

$(eval $(call BuildPackage,vitetris))
