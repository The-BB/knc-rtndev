# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2025 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=dislocker
PKG_VERSION:=0.7.3
PKG_RELEASE:=3

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=v$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/Aorimn/dislocker
PKG_MIRROR_HASH:=0772c3e0972aab1fe56f2662c0f861c5ed5f483a296cfa8aba286f245b47167b

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=LICENSE.txt

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/dislocker
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=Filesystem
  TITLE:=Read BitLocker encrypted volumes under Linux
  URL:=https://github.com/Aorimn/dislocker
  DEPENDS:=+libfuse +libmbedtls
endef

define Package/dislocker/description
 This software has been designed to read BitLocker encrypted partitions
 under a Linux system.
endef

define Package/dislocker/install
	$(INSTALL_DIR) $(1)/opt/bin $(1)/opt/lib
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/opt/bin/dislocker-{bek,file,fuse,metadata} \
		$(1)/opt/bin
	$(CP) $(PKG_INSTALL_DIR)/opt/bin/dislocker $(1)/opt/bin
	$(CP) $(PKG_INSTALL_DIR)/opt/lib/* $(1)/opt/lib
endef

$(eval $(call BuildPackage,dislocker))
