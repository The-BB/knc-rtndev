# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2025 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=daemonize
PKG_VERSION:=1.7.8
PKG_RELEASE:=2

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=release-$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/bmc/daemonize
PKG_MIRROR_HASH:=86aea65f1f12cb3ca3043afc1335cecb5e01f99f3223a09f8cd4b88853c8bd1d

PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE.md
PKG_MAINTAINER:=Entware team, https://entware.net

include $(INCLUDE_DIR)/package.mk

define Package/daemonize
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=runs a command as a daemon
  URL:=http://software.clapper.org/daemonize/
endef

define Package/daemonize/description
 daemonize is a command-line utility that runs a command as a Unix daemon.
endef

define Package/daemonize/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/daemonize $(1)/opt/bin
endef

$(eval $(call BuildPackage,daemonize))
