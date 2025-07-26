# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2025 Entware

# Abandoned in 2018

include $(TOPDIR)/rules.mk

PKG_NAME:=xmlstarlet
PKG_REAL_VERSION:=1.6.1
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2018-02-04
PKG_SOURCE_VERSION:=a7228161756b47e1348a6ad97bda10e511cb546a
PKG_SOURCE_URL:=https://git.code.sf.net/p/xmlstar/code
PKG_MIRROR_HASH:=b0eec2e74678acf188ad31b05718d4b7c221541f6c29e82fd84162ad13cc2b21

PKG_VERSION:=$(PKG_REAL_VERSION)_git$(subst -,,$(PKG_SOURCE_DATE))~$(call version_abbrev,$(PKG_SOURCE_VERSION))

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING Copyright

PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk

define Package/xmlstarlet
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=command line XML toolkit
  URL:=https://xmlstar.sourceforge.net/
  DEPENDS:=+libexslt +libxml2 +libxslt
endef

define Package/xmlstarlet/description
 XMLStarlet is a set of command line utilities (tools) which can
 be used to transform, query, validate, and edit XML documents and files using
 simple set of shell commands in similar way it is done for plain text files
 using UNIX grep, sed, awk, diff, patch, join, etc commands.
endef

CONFIGURE_ARGS += \
	--disable-build-docs

define Build/Prepare
	$(call Build/Prepare/Default)
	$(SED) "s|git describe --tags --dirty|echo $(PKG_VERSION)|g" $(PKG_BUILD_DIR)/configure.ac
	$(SED) "s|git describe --tags --dirty|echo $(PKG_VERSION)|g" $(PKG_BUILD_DIR)/Makefile.am
endef

define Package/xmlstarlet/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/xml $(1)/opt/bin
endef

$(eval $(call BuildPackage,xmlstarlet))
