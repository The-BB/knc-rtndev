# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2020-2025 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=scream-receiver
PKG_VERSION:=4.0
PKG_RELEASE:=2

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/duncanthrax/scream
PKG_MIRROR_HASH:=d0c8d5ca30e393329290f9706e9b6f8532b88ad7cdfcb74f1c7197184517afea

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=MS-PL
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/scream-receiver
  SECTION:=sound
  CATEGORY:=Sound
  TITLE:=Scream audio receiver
  URL:=https://github.com/duncanthrax/scream
  DEPENDS:=+libpcap +pulseaudio-daemon
endef

define Package/scream-receiver/description
 scream is a Scream audio receiver using Pulseaudio,
 ALSA or stdout as audio output.
endef

CMAKE_SOURCE_SUBDIR:=Receivers/unix

TARGET_LDFLAGS += \
	-Wl,-rpath-link=$(STAGING_DIR)/opt/lib/pulseaudio

define Package/scream-receiver/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/scream $(1)/opt/bin/scream-receiver
endef

$(eval $(call BuildPackage,scream-receiver))
