# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2025 Entware

# The newer versions based on cmake+vcpkg build system with online dependencies installation

include $(TOPDIR)/rules.mk

PKG_NAME:=megacmd
PKG_VERSION:=1.7.0
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_VERSION)_Linux
PKG_SOURCE_URL:=https://github.com/meganz/MEGAcmd
PKG_MIRROR_HASH:=2a03e5ba9624492fd546500207061cfff0fd76923246c24f121327415c222a04

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/megacmd
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=File Transfer
  TITLE:=Command Line Interactive and Scriptable Application
  URL:=https://github.com/meganz/megacmd
  DEPENDS:= \
	+icu +libcares +libcryptopp +libcurl +libmediainfo \
	+libpcre +libreadline +libsodium +libsqlite3 +libuv
endef

define Package/megacmd/description
 MEGAcmd provides non UI access to MEGA services. It intends to offer all the
 functionality with your MEGA account via commands.
endef

ifeq ($(CONFIG_USE_MUSL),y)
TARGET_CXXFLAGS += -fpermissive
endif

CONFIGURE_ARGS += \
    --disable-doxygen-doc \
    --without-freeimage \
    --without-ffmpeg

define Package/megacmd/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/mega-* $(1)/opt/bin
	$(INSTALL_DIR) $(1)/opt/lib
	$(CP) $(PKG_INSTALL_DIR)/opt/lib/libmega.so* $(1)/opt/lib
	$(SED) 's,^#!.*bash,#!/opt/bin/sh,' $(1)/opt/bin/*
endef

$(eval $(call BuildPackage,megacmd))
