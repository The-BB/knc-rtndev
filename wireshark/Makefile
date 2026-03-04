# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2020-2026 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=wireshark
PKG_VERSION:=4.6.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:= \
		https://1.eu.dl.wireshark.org/src \
		http://ftp.uni-kl.de/pub/wireshark/src/all-versions \
		https://wireshark.org/download/src/all-versions
PKG_HASH:=e218e3b3899e5d6e35a5fe95eeeabead587ed084cbf5fc330ac827f9a3137de8

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/wireshark
  SECTION:=net
  CATEGORY:=Network
  TITLE:=network protocol analyzer
  URL:=https://www.wireshark.org
  DEPENDS:= \
	+bcg729 +glib2 +krb5-libs +libcap +libcares +libgcrypt +libgnutls +liblz4 \
	+libmaxminddb +libnghttp2 +libopus +libpcap +libspandsp +libspeexdsp +libssh \
	+libxml2 +libxxhash +sbc +zstd
endef

define Package/wireshark/description
 Wireshark is the world’s foremost and widely-used network protocol analyzer.
endef

CMAKE_OPTIONS += \
	-DBUILD_wireshark=OFF \
	-DENABLE_LUA=OFF

define BuildNativeBins
	$(INSTALL_DIR) $(PKG_BUILD_DIR)/Bin-host

	( cd $(PKG_BUILD_DIR)/tools/lemon; \
		cmake -B $(PKG_BUILD_DIR)/build-native/lemon \
			-G "Ninja" -DCMAKE_BUILD_TYPE=Release; \
		cmake --build $(PKG_BUILD_DIR)/build-native/lemon -j$(NPROC); \
		$(CP) $(PKG_BUILD_DIR)/build-native/lemon/lemon \
			$(PKG_BUILD_DIR)/Bin-host; \
	)
endef

define Build/Compile
	$(call BuildNativeBins)
endef

define Package/wireshark/install
	$(INSTALL_DIR) $(1)/opt/lib/wireshark
	$(CP) $(PKG_INSTALL_DIR)/opt/bin $(1)/opt
	$(CP) $(PKG_INSTALL_DIR)/opt/lib/*.so* $(1)/opt/lib
	$(CP) $(PKG_INSTALL_DIR)/opt/lib/wireshark/plugins \
		$(1)/opt/lib/wireshark
	$(INSTALL_DIR) $(1)/opt/libexec
	$(CP) $(PKG_INSTALL_DIR)/opt/libexec/wireshark $(1)/opt/libexec
	$(INSTALL_DIR) $(1)/opt/share
	$(CP) $(PKG_INSTALL_DIR)/opt/share/wireshark $(1)/opt/share
endef

$(eval $(call BuildPackage,wireshark))
