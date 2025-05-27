# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2025 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=vorbis-tools
PKG_VERSION:=1.4.3
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=v$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/xiph/vorbis-tools
PKG_MIRROR_HASH:=83dc9f8f57e22428bc0ac29962a6cb54faa98bc4f07c846984443b7060aba528

PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING LICENCE.LGPL
PKG_MAINTAINER:=Entware team, https://entware.net

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/vorbis-tools
	SECTION:=sound
	CATEGORY:=Sound
	DEPENDS:=+libogg +libvorbis +libflac
	TITLE:=vorbis-tools and nothing else
	URL:=http://xiph.org/vorbis/
	MAINTAINER:=Entware team, https://entware.net
endef

define Package/vorbis-tools/description
 oggdec, oggenc, ogginfo, vcut, vorbiscomment command line utilities.
endef

CONFIGURE_ARGS += \
	--disable-ogg123 \
	--disable-oggtest \
	--disable-vorbistest \
	--disable-curltest

define Package/vorbis-tools/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/* $(1)/opt/bin
endef

$(eval $(call BuildPackage,vorbis-tools))
