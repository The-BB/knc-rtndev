# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2026 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=portspoof
PKG_VERSION:=1.4
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=a5d1a176b2a2cd35213c88615dd1ce1e6910b4d4
PKG_SOURCE_URL:=https://github.com/drk1wi/portspoof
PKG_MIRROR_HASH:=a63e417c592d85b537079e001f3320110d623c5c180e695aae4039868adf805f

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/portspoof
  SECTION:=net
  CATEGORY:=Network
  TITLE:=effective defense against port scanners
  URL:=$(PKG_SOURCE_URL)
  DEPENDS:=+libstdcpp
endef

define Package/portspoof/description
 The Portspoof program primary goal is to enhance OS security through a set of
 few techniques: all TCP ports are always open, every open TCP port emulates
 a services. Portspoof can be used as an 'Exploitation Framework Frontend',
 that turns your system into responsive and aggressive machine.
endef

define Package/portspoof/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/portspoof $(1)/opt/bin
	$(INSTALL_DIR) $(1)/opt/etc
	$(INSTALL_CONF) \
	    $(PKG_INSTALL_DIR)/opt/etc/portspoof{.conf,_signatures} $(1)/opt/etc
endef

$(eval $(call BuildPackage,portspoof))
