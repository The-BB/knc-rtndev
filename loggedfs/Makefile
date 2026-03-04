# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2025 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=loggedfs
PKG_VERSION:=0.9
# libxml2
PKG_RELEASE:=4

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/rflament/loggedfs/archive
PKG_HASH:=10cd007782c6b91a154758dabac0c3b41e580ca0f9496cab411054219ef52b22

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/loggedfs
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=Filesystem
  TITLE:=Filesystem monitoring with Fuse
  URL:=https://www.loggedfs.org
  DEPENDS:=+fuse-utils +libpcre2 +libstdcpp +libxml2
endef

define Package/loggedfs/description
 LoggedFS is a transparent fuse-filesystem which allows you to log
 every operation that happens in the backend filesystem. Logs can be written
 to syslog, to a file, or to standard output. It comes with an XML configuration
 file in which you can choose exactly what you want to log. You can add filters
 on users, operations (open, read, write, chown, chmod, etc.), filenames, and
 return codes. Filename's filters are regular expressions. Since it is fuse-based,
 you don't need to change anything in your kernel or hard disk partition to use it.
endef

define Package/loggedfs/install
	$(INSTALL_DIR) $(1)/opt/bin $(1)/opt/etc
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/loggedfs $(1)/opt/bin
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/loggedfs.xml $(1)/opt/etc
endef

$(eval $(call BuildPackage,loggedfs))
