# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2025 Entware

# Abandoned in 2019

include $(TOPDIR)/rules.mk

PKG_NAME:=movgrab
PKG_VERSION:=3.1.2
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/ColumPaget/Movgrab
PKG_MIRROR_HASH:=2122ab366ff10001eca3b915425eaaf8ec31b21b71604c46ed00f7abdff52cb1

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=GPL-3.0-or-later
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk

define Package/movgrab
  SECTION:=multimedia
  CATEGORY:=Multimedia
  TITLE:=downloader for videos from various websites
  URL:=https://sites.google.com/site/columscode/home/movgrab
  DEPENDS:=+libopenssl +zlib
endef

define Package/movgrab/description
  Movgrab is a command line tool for downloading video clips from
 websites such as YouTube, Daily Motion, Break.com, Vimeo, Blip.tv, Liveleak
 and others.
endef

ifeq ($(CONFIG_GCC_USE_VERSION_14),y)
TARGET_CFLAGS += -std=gnu89
endif

TARGET_CFLAGS += $(TARGET_CPPFLAGS) $(TARGET_LDFLAGS)

CONFIGURE_ARGS += \
	--prefix=/opt \
	--enable-ssl \
	--enable-largefiles

define Build/Configure
	rm -f $(PKG_BUILD_DIR)/libUseful-2.0/*.{o,a,so}
	$(call Build/Configure/Default)
endef

define Package/movgrab/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/movgrab $(1)/opt/bin
endef

$(eval $(call BuildPackage,movgrab))
