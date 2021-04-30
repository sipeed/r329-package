#
# Copyright (C) 2007-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-numpy
PKG_VERSION:=1.19.2
PKG_RELEASE:=1
PKG_LICENSE:=BSD

PKG_SOURCE:=numpy-$(PKG_VERSION).zip

PKG_BUILD_DIR:=$(COMPILE_DIR)/numpy-$(PKG_VERSION)

include $(BUILD_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/$(PKG_NAME)
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=python3 numpy
  DEPENDS:=+python3 +python3-cython
  URL:=https://pypi.org/project/numpy/
endef

define Package/$(PKG_NAME)/description
NumPy: array processing for numbers, strings, records, and objects.
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,,\
		install --root="$(PKG_INSTALL_DIR)" --prefix="/usr" \
	)
endef

define Py3Package/python3-numpy/filespec
+|$(PYTHON3_PKG_DIR)
endef

define Package/python3-numpy/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call Py3Package,python3-numpy))
$(eval $(call BuildPackage,python3-numpy))
