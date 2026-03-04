# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2025 Entware

# Abandoned in 2018

include $(TOPDIR)/rules.mk

PKG_NAME:=daemontools-encore
PKG_VERSION:=1.11
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/bruceg/daemontools-encore
PKG_MIRROR_HASH:=fe58cf45587a8e3c4f72eb2f91f60c364128be1cb74d14b23a2b7ff2ddc978cf

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk

define Package/daemontools-encore
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=a collection of tools for managing UNIX services
  URL:=http://untroubled.org/daemontools-encore/
endef

define Package/daemontools-encore/description
 A collection of tools for managing UNIX services.
endef

ifeq ($(CONFIG_GCC_USE_VERSION_14),y)
TARGET_CFLAGS += -std=c99 -ansi -D_DEFAULT_SOURCE -D_POSIX_SOURCE
endif

define Build/Configure
	echo "$(TARGET_CC) $(TARGET_CFLAGS)" > $(PKG_BUILD_DIR)/conf-cc
	echo "$(TARGET_CC) $(TARGET_LDFLAGS)" > $(PKG_BUILD_DIR)/conf-ld
	( cd $(PKG_BUILD_DIR); ./makemake; )
endef

define Package/daemontools-encore/install
	$(INSTALL_DIR) $(1)/opt/bin
	( cd $(PKG_BUILD_DIR); \
		cat BIN | cut -d ':' -f 6 | \
		xargs -n 1 -I % cp --parents "%" $(1)/opt/bin; \
	)
	$(INSTALL_DIR) $(1)/opt/etc/init.d
	$(INSTALL_BIN) ./files/S03daemontools-encore $(1)/opt/etc/init.d
	$(INSTALL_DIR) $(1)/opt/var/service
endef

$(eval $(call BuildPackage,daemontools-encore))
