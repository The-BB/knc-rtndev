# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2017-2026 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=entware-release
PKG_VERSION:=2026.04
PKG_RELEASE:=1

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=GPL-2.0-only
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/kernel.mk

define Package/entware-release
  SECTION:=base
  CATEGORY:=Base system
  TITLE:=Entware release information
  URL:=https://entware.net
  PKGARCH:=all
  PKG_DEFAULT_DEPENDS:=
endef

define Package/entware-release/description
 entware_release is a file in /opt/etc with entware info.
endef

ifneq ($(firstword "x$(CONFIG_CPU_TYPE)"), "x")
CPUTYPE=$(CONFIG_CPU_TYPE)
else
CPUTYPE=unknown
endif
CPUSUBTYPE=$(if $(CONFIG_CPU_SUBTYPE),$(CONFIG_CPU_SUBTYPE),unknown)
FLOAT=$(if $(CONFIG_SOFT_FLOAT),soft,hard)

ENVCFLAGS:=$(TARGET_OPTIMIZATION) $(call qstrip,$(CONFIG_EXTRA_OPTIMIZATION))
ifeq ($(CONFIG_SOFT_FLOAT),y)
    ifeq ($(CONFIG_arm),y)
        ENVCFLAGS+= -mfloat-abi=soft
    else
        ENVCFLAGS+= -msoft-float
    endif
endif

ifeq ($(CONFIG_USE_GLIBC),y)
LIBCTYPE=glibc
LIBC_VERSION=$(call qstrip,$(CONFIG_GLIBC_VERSION))
endif

ifeq ($(CONFIG_USE_MUSL),y)
LIBCTYPE=musl
LIBC_VERSION=$(call qstrip,$(CONFIG_MUSL_VERSION))
endif

ifeq ($(CONFIG_USE_APK),y)
PM=APK (Alpine Package Keeper)
else
PM=OPKG (Open PacKaGe Management)
endif

# skip steps
Build/Prepare:=:
Build/Configure:=:
Build/Compile:=:

define Package/entware-release/install
	$(INSTALL_DIR) $(1)/opt/etc
	echo "PRETTY_NAME=\"Entware Keenetic/NetCraze $(PKG_VERSION)\"" > $(1)/opt/etc/entware_release
	echo "NAME=\"Entware Keenetic/NetCraze\"" >> $(1)/opt/etc/entware_release
	echo "VERSION_ID=\"$(PKG_VERSION)\"" >> $(1)/opt/etc/entware_release
	echo "VERSION=\"$(PKG_VERSION) (sync with OpenWrt)\"" >> $(1)/opt/etc/entware_release
	echo "ID=entware" >> $(1)/opt/etc/entware_release
	echo "HOME_URL=\"empty\"" >> $(1)/opt/etc/entware_release
	echo "SUPPORT_URL=\"empty\"" >> $(1)/opt/etc/entware_release
	echo "BUG_REPORT_URL=\"empty\"" >> $(1)/opt/etc/entware_release
	echo "" >> $(1)/opt/etc/entware_release
	echo "Build summary:" >> $(1)/opt/etc/entware_release
	echo "Linux Kernel Version: $(LINUX_VERSION)" >> $(1)/opt/etc/entware_release
	echo "CPU Architecture: $(ARCH)" >> $(1)/opt/etc/entware_release
	echo "CPU Type: $(CPUTYPE)" >> $(1)/opt/etc/entware_release
	echo "CPU SubType: $(CPUSUBTYPE)" >> $(1)/opt/etc/entware_release
	echo "Floating Point: $(FLOAT)" >> $(1)/opt/etc/entware_release
	echo "Binutils Version: $(call qstrip,$(CONFIG_BINUTILS_VERSION))" >> $(1)/opt/etc/entware_release
	echo "GCC Version: $(call qstrip,$(CONFIG_GCC_VERSION))" >> $(1)/opt/etc/entware_release
	echo "GCC Flags: \"$(ENVCFLAGS)\"" >> $(1)/opt/etc/entware_release
	echo "C Library: $(LIBCTYPE)" >> $(1)/opt/etc/entware_release
	echo "C Library Version: $(LIBC_VERSION)" >> $(1)/opt/etc/entware_release
	echo "" >> $(1)/opt/etc/entware_release
	echo "Package Manager: $(PM)" >> $(1)/opt/etc/entware_release
endef

$(eval $(call BuildPackage,entware-release))
