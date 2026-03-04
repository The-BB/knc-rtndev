# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2026 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=urbackup-server
PKG_VERSION:=2.5.35
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:= \
		http://hndl.urbackup.org/Server/$(PKG_VERSION) \
		https://www.urbackup.org/downloads/Server/$(PKG_VERSION)
PKG_HASH:=3505796b622e9e34c3093585d295eb850114d85d5ea69ecaa8b0f8939ed3a1b9

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=AGPL-3.0-or-later
PKG_LICENSE_FILES:=COPYING

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/urbackup-server
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=UrBackup Server
  URL:=http://www.urbackup.org/
  DEPENDS:=+libcurl +libstdcpp +zlib +zstd
endef

define Package/urbackup-server/description
 UrBackup is an easy to setup Open Source client/server backup system.
endef

CONFIGURE_ARGS += \
	--enable-embedded-cryptopp \
	--oldincludedir="$(STAGING_DIR)/opt/include"

ifeq ($(CONFIG_USE_MUSL),y)
TARGET_CXXFLAGS += -D_LARGEFILE64_SOURCE
endif

TARGET_LDFLAGS += $(if $(CONFIG_GCC_LIBSSP),-lssp)

define Package/urbackup-server/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/* $(1)/opt/bin
	$(INSTALL_DIR) $(1)/opt/share/urbackup
	$(CP) $(PKG_INSTALL_DIR)/opt/share/urbackup/* $(1)/opt/share/urbackup
	$(INSTALL_DIR) $(1)/opt/etc/init.d
	$(INSTALL_BIN) ./files/S60urbackup-server $(1)/opt/etc/init.d
endef

$(eval $(call BuildPackage,urbackup-server))
