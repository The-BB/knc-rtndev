# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2025 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=iprange
PKG_VERSION:=1.0.4
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/firehol/iprange/tar.gz/refs/tags/v$(PKG_VERSION)?
PKG_HASH:=17732630a014d233807a20a4abbd7cdf2a930c92fcc1b4e5ca2a55e9c0ea4973

PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING
PKG_MAINTAINER:=Entware team, https://entware.net

PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

define Package/iprange
  SECTION:=net
  CATEGORY:=Network
  TITLE:=manage IP ranges
  URL:=http://firehol.org
endef

define Package/iprange/description
 Manage IP ranges.
endef

CONFIGURE_ARGS += \
	--disable-man

define Package/iprange/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/iprange $(1)/opt/bin
endef

$(eval $(call BuildPackage,iprange))
