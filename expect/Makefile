# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2020-2026 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=expect
PKG_VERSION:=5.45.4
PKG_RELEASE:=2

PKG_SOURCE:=$(PKG_NAME)$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=@SF/expect
PKG_HASH:=49a7da83b0bdd9f46d04a04deec19c7767bb9a323e40c4781f89caf760b92c34

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)$(PKG_VERSION)

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=Public Domain
PKG_LICENSE_FILES:=license.terms

PKG_FIXUP:=autoreconf
PKG_REMOVE_FILES:=testsuite/configure.in
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/expect
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Expect
  URL:=https://www.nist.gov/services-resources/software/expect
  DEPENDS:=+tcl
endef

define Package/expect/description
 Expect is a tool for automating interactive applications such as
 telnet, ftp, passwd, fsck, rlogin, ssh, tip, etc.
endef

CONFIGURE_ARGS += \
	--with-tcl=$(STAGING_DIR)/opt/lib

MAKE_FLAGS += \
	RANLIB=":"

define Package/expect/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(CP) $(PKG_INSTALL_DIR)/opt/bin/expect* $(1)/opt/bin
	$(INSTALL_DIR) $(1)/opt/lib/
	$(CP) $(PKG_INSTALL_DIR)/opt/lib/$(PKG_NAME)$(PKG_VERSION) $(1)/opt/lib
endef

$(eval $(call BuildPackage,expect))
