# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2019-2026 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=nmon
PKG_VERSION:=16s
PKG_RELEASE:=1

PKG_SOURCE:=lmon$(PKG_VERSION).c
PKG_SOURCE_URL:=@SF/nmon
PKG_HASH:=0736ce0f729e48c124a7ba566c069c5a234511cc9c6ac9277da92f8bb44f2b11

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=GPL-3.0-or-later
PKG_LICENSE_FILES:=$(PKG_SOURCE)

UNPACK_CMD=$(CP) $(DL_DIR)/$(PKG_SOURCE) $(1)

include $(INCLUDE_DIR)/package.mk

define Package/nmon
  SECTION:=nmon
  CATEGORY:=Administration
  TITLE:=Nigel's performance Monitor for Linux
  URL:=https://nmon.sourceforge.io/pmwiki.php
  DEPENDS:=+libncursesw
endef

define Package/nmon/description
 Linux performance monitoring on-screen or to CSV file.
endef

TARGET_CFLAGS += -D $(ARCH) -D Entware
TARGET_LDFLAGS += -lncursesw -lm

define Build/Compile
	$(TARGET_CC) $(PKG_BUILD_DIR)/$(MAKE_PATH)/$(PKG_SOURCE) -o \
		$(PKG_BUILD_DIR)/$(PKG_NAME) $(TARGET_CFLAGS) $(TARGET_LDFLAGS)
endef

define Package/nmon/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(CP) $(PKG_BUILD_DIR)/$(PKG_NAME) $(1)/opt/bin
endef

$(eval $(call BuildPackage,nmon))
