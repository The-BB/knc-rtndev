# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2020-2025 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=brlaser
PKG_VERSION:=6
PKG_RELEASE:=2

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=v$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/pdewacht/brlaser
PKG_MIRROR_HASH:=92002ab26fe5776e16d3780060166ece722d67a43b5183020af0e35443a4bc47

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/brlaser
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=Printing
  TITLE:=Brother laser printer driver
  URL:=https://github.com/pdewacht/brlaser
  DEPENDS:=+cups
endef

define Package/brlaser/description
 Brlaser is a CUPS driver for Brother laser printers without PCL/PostScript
 language support.
endef

TARGET_CFLAGS += -I$(STAGING_DIR)/opt/include

define Package/brlaser/install
	$(INSTALL_DIR) $(1)/opt
	$(CP) $(PKG_INSTALL_DIR)/opt/{lib,share} $(1)/opt
endef

$(eval $(call BuildPackage,brlaser))
