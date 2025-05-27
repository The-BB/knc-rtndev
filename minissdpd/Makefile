# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2025 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=minissdpd
PKG_VERSION:=2.3.9
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=b9f21a9cfe9d90afbd87dcff290a8dc8c078409b
PKG_SOURCE_URL:=https://github.com/miniupnp/miniupnp
PKG_MIRROR_HASH:=db3edf0e3fe0dd4d0aaa45dcef5a8e3994616df9d0fac9288dd6df227d456ad8

PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Entware team, https://entware.net

include $(INCLUDE_DIR)/package.mk

MAKE_PATH:=$(PKG_NAME)

define Package/minissdpd
  SECTION:=net
  CATEGORY:=Network
  TITLE:=SSDP daemon
  URL:=http://miniupnp.free.fr/minissdpd.html
  DEPENDS:=+libnfnetlink
endef

define Package/minissdpd/description
 MiniSSDPd is a daemon that:
 1 - keeps track of all UPnP devices announcing themselves on the network.
 its database can be queried by local processes using a protocol based on
 a unix socket. That enables local processes to quickly discover UPnP devices
 without broadcasting SSDP message and waiting several seconds for a response.
 2 - keeps a database of local UPnP devices hosted on the machine and
 answering SSDP searchs on their behalf. It enables to run several UPnP devices,
 like an IGD and a MediaServer, on the same machine.
endef

define Package/gnuchess/conffiles
/opt/etc/config/minissdpd.conf
endef

define Package/minissdpd/install
	$(INSTALL_DIR) $(1)/opt/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/$(PKG_NAME)/$(PKG_NAME) $(1)/opt/sbin
	$(INSTALL_DIR) $(1)/opt/etc/init.d
	$(INSTALL_BIN) files/S11minissdpd $(1)/opt/etc/init.d
	$(INSTALL_DIR) $(1)/opt/etc/config
	$(INSTALL_CONF) files/minissdpd.conf $(1)/opt/etc/config
endef

$(eval $(call BuildPackage,minissdpd))
