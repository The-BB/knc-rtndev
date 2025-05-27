# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2025 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=par2cmdline
PKG_VERSION:=1.0.0
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=v$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/Parchive/par2cmdline
PKG_MIRROR_HASH:=a4645eb682e4ea421d4d08f7313c26cd4b54a586bf59af73cc775a620171403d

PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING
PKG_MAINTAINER:=Entware team, https://entware.net

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/par2cmdline
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=file verification and repair tool
  URL:=https://parchive.github.io
  DEPENDS:=+libstdcpp
endef

define Package/par2cmdline/description
 par2cmdline is a PAR 2.0 compatible file verification and repair tool.
endef

define Package/par2cmdline/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/par2 $(1)/opt/bin
	$(FIND) $(PKG_INSTALL_DIR)/opt/bin -type l -exec $(CP) -a {} $(1)/opt/bin \;
endef

$(eval $(call BuildPackage,par2cmdline))
