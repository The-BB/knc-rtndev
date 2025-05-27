# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2025 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=bochs
PKG_VERSION:=3.0
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=REL_$(subst .,_,$(PKG_VERSION))_FINAL
PKG_SOURCE_URL:=https://github.com/bochs-emu/Bochs
PKG_MIRROR_HASH:=d14dda59324f7efcb43f22e5db275c64464f889d745c9fe1c384c8026efdb941

PKG_LICENSE:=LGPL-2.1-or-later
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Entware team, https://entware.net

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/bochs
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=x86 PC emulator
  URL:=https://bochs.sourceforge.io
  DEPENDS:=+libncursesw +libstdcpp
endef

define Package/bochs/description
 Bochs is a highly portable open source IA-32 (x86) PC emulator written in C++,
 that runs on most popular platforms. It includes emulation of the Intel x86 CPU,
 common I/O devices, and a custom BIOS.
endef

CONFIGURE_PATH:=bochs
MAKE_PATH:=$(CONFIGURE_PATH)

CONFIGURE_ARGS += \
	--without-x11 \
	--disable-readline \
	--with-nogui \
	--with-rfb \
	--with-term \
	--disable-disasm \
	--disable-docbook \
	--enable-ne2000 \
	--enable-pnic \
	--enable-e1000

TARGET_CFLAGS += \
	-I$(STAGING_DIR)/opt/include

TARGET_LDFLAGS += \
	-lncurses \
	-lpthread

define Package/bochs/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/{bochs,bximage} \
		$(1)/opt/bin
	$(INSTALL_DIR) $(1)/opt/share
	$(CP) $(PKG_INSTALL_DIR)/opt/share/bochs \
		$(1)/opt/share
endef

$(eval $(call BuildPackage,bochs))
