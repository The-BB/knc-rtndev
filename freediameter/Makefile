# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2020-2026 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=freediameter
PKG_VERSION:=1.6.0
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/freeDiameter/freeDiameter
PKG_MIRROR_HASH:=26a0bcfad5fc328837dd2a29307d9c12ebe9694b2fc1a527343c1025de3811d2

PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Entware team, https://entware.net

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk
include $(INCLUDE_DIR)/nls.mk

define Package/freediameter
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Diameter proto implementation
  URL:=http://www.freediameter.net
  DEPENDS:=+libgcrypt +libgnutls +libidn2
endef

define Package/freediameter/description
 freeDiameter provides an extensible platform for deploying a
 Diameter network for your Authentication, Authorization and Accounting
 needs, whether you are involved in research or a network operator.
endef

CMAKE_OPTIONS += \
	-DDISABLE_SCTP=YES

define Package/freediameter/install
	$(INSTALL_DIR) $(1)/opt
	$(CP) $(PKG_INSTALL_DIR)/opt/{bin,lib} $(1)/opt
endef

$(eval $(call BuildPackage,freediameter))
