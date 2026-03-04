# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2026 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=fzy
PKG_VERSION:=1.1
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=d811eaf9d73593f8293a73f98a17b36f016873e6
PKG_SOURCE_URL:=https://github.com/jhawthorn/fzy
PKG_MIRROR_HASH:=7cad43f5d60e94d126da30e8ea309172fd01349a7b71fb14d59d24abdbaf251b

include $(INCLUDE_DIR)/package.mk

define Package/fzy
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=Filesystem
  TITLE:=fuzzy finder for the terminal
  URL:=$(PKG_SOURCE_URL)
  MAINTAINER:=Entware team, https://entware.net
endef

define Package/fzy/description
 fzy is a fast, simple fuzzy text selector for the terminal
 with an advanced scoring algorithm.
endef

define Package/fzy/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/fzy $(1)/opt/bin
endef

$(eval $(call BuildPackage,fzy))
