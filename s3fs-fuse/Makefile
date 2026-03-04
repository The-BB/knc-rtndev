# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2026 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=s3fs-fuse
PKG_VERSION:=1.97
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=v$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/s3fs-fuse/s3fs-fuse
PKG_MIRROR_HASH:=a1895b52692b5fc2cd8babb7dbb86964f09811cfaba7b0c797cbd8ddcf71c3ca

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=GPL-2.0-only
PKG_LICENSE_FILES:=COPYING

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk

define Package/s3fs-fuse
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Filesystem
  TITLE:=FUSE filesystem for Amazon S3
  URL:=https://github.com/s3fs-fuse/s3fs-fuse
  DEPENDS:=+libcurl +libfuse3 +libstdcpp +libxml2
endef

define Package/s3fs-fuse/description
 FUSE-based file system backed by Amazon S3.
endef

CONFIGURE_ARGS += \
	--with-openssl

ifeq ($(or $(CONFIG_mips),$(CONFIG_mipsel)),y)
  TARGET_LDFLAGS += -latomic
endif

define Package/s3fs-fuse/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/s3fs $(1)/opt/bin
endef

$(eval $(call BuildPackage,s3fs-fuse))
