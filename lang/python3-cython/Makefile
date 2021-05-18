#
# Copyright (C) 2007-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-cython
PKG_VERSION:=0.29.2
PKG_RELEASE:=1
PKG_LICENSE:=Apache

PKG_SOURCE:=Cython-$(PKG_VERSION).tar.gz

PKG_BUILD_DIR:=$(COMPILE_DIR)/Cython-$(PKG_VERSION)

include $(BUILD_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/$(PKG_NAME)
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=python3 Cython
  DEPENDS:= +python3
  URL:=https://cython.org/
endef

define Package/$(PKG_NAME)/description
Cython is an optimising static compiler for both the Python programming language and the extended Cython programming language (based on Pyrex).
endef

define Build/Compile
	$(call HostPython3, \
		__PYVENV_LAUNCHER__="/usr/bin/$(PYTHON3)" \
		$(3) \
		, \
		-m pip install cython --root="/" --prefix="$(OUT_DIR)/host" \
	)
	$(call Build/Compile/Py3Mod,,\
		install --root="$(PKG_INSTALL_DIR)" --prefix="/usr" \
	)
endef

define Py3Package/$(PKG_NAME)/filespec
+|$(PYTHON3_PKG_DIR)
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call Py3Package,$(PKG_NAME)))
$(eval $(call BuildPackage,$(PKG_NAME)))
