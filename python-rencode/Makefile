# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2011-2026 Entware

include $(TOPDIR)/rules.mk

PKG_NAME:=rencode
PKG_VERSION:=1.0.6
PKG_RELEASE:=4

PYPI_NAME:=rencode
PKG_HASH:=2586435c4ea7d45f74e26765ad33d75309de7cf47c4d762e8efabd39905c0718

PKG_MAINTAINER:=Entware team, https://entware.net
PKG_LICENSE:=GPL-3.0-only
PKG_LICENSE_FILES:=COPYING

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-rencode
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Web safe object pickling/unpickling
  URL:=https://github.com/aresch/rencode
  DEPENDS:=+python3
endef

define Package/python3-rencode/description
 The rencode module is similar to bencode from the BitTorrent project.
endef

define Package/python3-rencode/postrm
#!/bin/sh

rm -rf $(PYTHON3_PKG_DIR)/$(PYPI_NAME)
rm -rf $(PYTHON3_PKG_DIR)/$(PYPI_NAME)-$(PKG_VERSION).dist-info
endef

$(eval $(call Py3Package,python3-rencode))
$(eval $(call BuildPackage,python3-rencode))
