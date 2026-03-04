# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2006-2011 OpenWrt.org
# Copyright (C) 2015-2026 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=ffmpegthumbnailer
PKG_VERSION:=2.3.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/dirkvdb/ffmpegthumbnailer/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=ddf561e294385f07d0bd5a28d0aab9de79b8dbaed29b576f206d58f3df79b508

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=GPL-2.0-only
PKG_LICENSE_FILES:=COPYING

CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/libffmpegthumbnailer
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=library to create thumbnails
  URL:=https://github.com/dirkvdb/ffmpegthumbnailer
  DEPENDS:=+libffmpeg-full +libjpeg +libpng +libstdcpp
endef

define Package/libffmpegthumbnailer/description
 libffmpegthumbnailer is a library that can be used to create thumbnails
 for your video files.
endef

define Package/libffmpegthumbnailer/install
	$(INSTALL_DIR) $(1)/opt/lib
	$(CP) $(PKG_INSTALL_DIR)/opt/lib/libffmpegthumbnailer*.so* $(1)/opt/lib
endef

$(eval $(call BuildPackage,libffmpegthumbnailer))
