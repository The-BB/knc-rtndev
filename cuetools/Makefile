# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2025 Entware

# Abandoned in 2020

include $(TOPDIR)/rules.mk

PKG_NAME:=cuetools
PKG_VERSION:=1.4.1
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/svend/cuetools
PKG_MIRROR_HASH:=2d346cd995b8d3a58d6e05d8cfa3839f79df1ce7a035fbe662f35af7064075e1

PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING
PKG_MAINTAINER:=Entware team, https://entware.net

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/cuetools
  SECTION:=sound
  CATEGORY:=Sound
  TITLE:=cue and toc file parsers and utilities
  URL:=https://github.com/svend/cuetools
endef

define Package/cuetools/description
 cuetools is a set of utilities for working with Cue Sheet (cue) and
 Table of Contents (toc) files.
endef

define Package/cuetools/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/* $(1)/opt/bin
endef

$(eval $(call BuildPackage,cuetools))
