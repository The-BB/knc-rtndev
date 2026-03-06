# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2026 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=vorbis-tools
PKG_VERSION:=1.4.3
PKG_RELEASE:=2

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=v$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/xiph/vorbis-tools
PKG_MIRROR_HASH:=e9d31600e575d22641ed0d0245ef02bb4e89900b06e7086a73554371a66e23f8

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=GPL-2.0-only LGPL-2.0-only
PKG_LICENSE_FILES:=COPYING LICENCE.LGPL

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/vorbis-tools
  SECTION:=sound
  CATEGORY:=Sound
  TITLE:=tools for working with Ogg Vorbis audio
  URL:=https://xiph.org/vorbis/
  DEPENDS:=+libflac +libogg +libvorbis
endef

define Package/vorbis-tools/description
 oggdec, oggenc, ogginfo, vcut, vorbiscomment command line utilities.
endef

CONFIGURE_ARGS += \
	--disable-curltest \
	--disable-ogg123 \
	--disable-oggtest \
	--disable-vorbistest

define Package/vorbis-tools/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/* $(1)/opt/bin
endef

$(eval $(call BuildPackage,vorbis-tools))
