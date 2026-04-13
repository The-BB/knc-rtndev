# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2016-2026 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=go
PKG_VERSION:=1.26.2
PKG_RELEASE:=1

PKG_SOURCE:=go$(PKG_VERSION).src.tar.gz
PKG_SOURCE_URL:= \
		https://go.dev/dl/ \
		https://golang.google.cn/dl/ \
		https://mirrors.nju.edu.cn/golang/ \
		https://mirrors.ustc.edu.cn/golang/
PKG_HASH:=2e91ebb6947a96e9436fb2b3926a8802efe63a6d375dffec4f82aa9dbd6fd43b

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/golang/go_env.mk

PKG_UNPACK += --strip-components=1 -C $(PKG_BUILD_DIR)

define Package/go/Default
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=The Go Programming Language
  URL:=https://golang.org/
  PROVIDES:=go
endef

define Package/go
  $(call Package/go/Default)
  VARIANT:=hf
  DEFAULT_VARIANT:=1
endef

define Package/go_nohf
  $(call Package/go/Default)
  VARIANT:=nohf
  DEPENDS:=@arm
endef

define Package/go/description
 Go is an open source programming language that makes it
 easy to build simple, reliable, and efficient software.
endef

Package/go_nohf/description=$(Package/go/description)

BINTYPE:=$(shell uname -m | sed 's/aarch64/arm64/;s/i[3-6]86/386/;s/x86_64/amd64/')

RSTRIP:=:
STRIP:=:

Build/Configure:=:

define Build/Compile
	( \
		cd $(PKG_BUILD_DIR)/src; \
		$(GO_VARS) GO_LDFLAGS="-s -w" PKG_CONFIG=/opt/bin/pkg-config \
		GOROOT_BOOTSTRAP=$(STAGING_DIR_HOST)/go ./make.bash --no-banner; \
	)
# https://github.com/golang/go/commit/2e97c30d8d9f5740a503428c09efae7bedb68efb
# remove .../src/debug/elf/testdata/libtiffxx.so_ or fix deps (add lib{tiff,stdcpp}
	rm -f $(PKG_BUILD_DIR)/src/debug/elf/testdata/libtiffxx.so_
	if [ -d "$(PKG_BUILD_DIR)/bin/linux_$(GOARCH)" ]; then \
		rm $(PKG_BUILD_DIR)/bin/go{,fmt}; \
		mv $(PKG_BUILD_DIR)/bin/linux_$(GOARCH)/* $(PKG_BUILD_DIR)/bin/; \
		rm -rf $(PKG_BUILD_DIR)/{bin,pkg}/linux_$(GOARCH); \
	fi
	[ "$(BINTYPE)" = "$(GOARCH)" ] || rm -rf $(PKG_BUILD_DIR)/pkg/linux_$(BINTYPE)
	[ "$(BINTYPE)" = "$(GOARCH)" ] || rm -rf $(PKG_BUILD_DIR)/pkg/tool/linux_$(BINTYPE)
endef

define Package/go/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_DIR) $(1)/opt/lib/go
	$(CP) $(PKG_BUILD_DIR)/{api,bin,lib,misc,pkg,test,doc,src} $(1)/opt/lib/go
	$(LN) ../lib/go/bin/go $(1)/opt/bin/go
	$(LN) ../lib/go/bin/gofmt $(1)/opt/bin/gofmt
	# Entware specific: fix exec path in scripts
	$(FIND) $(1)/opt/lib/go -type f | $(XARGS) $(SED) \
		's,^#!.*bash,#!/opt/bin/bash,;s,^#!.*perl,#!/opt/bin/perl,'
endef

Package/go_nohf/install=$(Package/go/install)

define Package/go/extra_provides
	echo 'libc.so.6'
endef

Package/go_nohf/extra_provides=$(Package/go/extra_provides)

$(eval $(call BuildPackage,go))
$(eval $(call BuildPackage,go_nohf))
