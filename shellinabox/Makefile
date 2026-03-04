# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2017-2026 Entware

# Initial port of shellinabox to OpenWrt - Jan Jaeger 25-MAR-2010
# Makefile from OnionIoT/OpenWRT-Packages was used as a start

include $(TOPDIR)/rules.mk

PKG_NAME:=shellinabox
PKG_VERSION:=2.21
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=4f0ecc31ac6f985e0dd3f5a52cbfc0e9251f6361
PKG_SOURCE_URL:=https://github.com/shellinabox/shellinabox
PKG_MIRROR_HASH:=4859401b040d3df0fd96a3cd88300383a1b20abde1b6a49471f85f3ff0df7cde

PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

define Package/shellinabox
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Shell In A Box
  URL:=https://github.com/shellinabox/shellinabox
  DEPENDS:=+libopenssl
endef

define Package/shellinabox/description
 Web based AJAX terminal emulator.
endef

CONFIGURE_ARGS += \
	--disable-pam \
	--disable-runtime-loading \
	--bindir="/opt/sbin"

ifeq ($(CONFIG_USE_MUSL),y)
CONFIGURE_ARGS += \
	--disable-utmp
endif

define Package/shellinabox/install
	$(INSTALL_DIR) $(1)/opt/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/shellinaboxd $(1)/opt/sbin
	$(INSTALL_DIR) $(1)/opt/etc/init.d
	$(INSTALL_BIN) ./files/S88shellinaboxd $(1)/opt/etc/init.d
	$(INSTALL_DIR) $(1)/opt/lib/shellinabox
	$(INSTALL_DATA) \
	    $(PKG_BUILD_DIR)/shellinabox/{black-on-white,color,monochrome,white-on-black}.css \
	    $(1)/opt/lib/shellinabox
endef

$(eval $(call BuildPackage,shellinabox))
