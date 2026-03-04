# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2017-2025 Entware

# Ported to Entware from https://github.com/helmiau/badvpn_corkscrew
# Project archieved

include $(TOPDIR)/rules.mk

PKG_NAME:=badvpn
PKG_VERSION:=1.999.133
PKG_RELEASE=2

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=07268f02706e78e282e19641b5d1d41e8e89bf31
PKG_SOURCE_URL:=https://github.com/ambrop72/badvpn
PKG_MIRROR_HASH:=ca982200a9458e5d15dd5f3c9cefc80bd5eca4a76b6858577b6be248339e4f2b

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/badvpn
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=VPN
  TITLE:=peer-to-peer VPN system
  URL:=https://github.com/ambrop72/badvpn
endef

define Package/badvpn/description
 The tun2socks program "socksifes" TCP connections at the network layer.
 It implements a TUN device which accepts all incoming TCP connections (regardless of destination IP),
 and forwards the connections through a SOCKS server. This allows you to forward all connections through SOCKS,
 without any need for application support. It can be used, for example, to forward connections through a remote SSH server.
endef

CMAKE_OPTIONS += \
	-DBUILD_NOTHING_BY_DEFAULT=1 \
	-DBUILD_TUN2SOCKS=1 \
	-DBUILD_UDPGW=1

define Package/badvpn/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/badvpn-tun2socks $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/badvpn-udpgw $(1)/opt/bin
endef

$(eval $(call BuildPackage,badvpn))
