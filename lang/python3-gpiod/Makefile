#
# Copyright (C) 2019-2O20 CZ.NIC, z. s. p. o. (https://www.nic.cz/)
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-gpiod
PKG_VERSION:=1.5.0
PKG_RELEASE:=2

PKG_SOURCE:=gpiod-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/junhuanchen/python3-gpiod/files/6447504/

PKG_BUILD_DIR:=$(COMPILE_DIR)/gpiod-$(PKG_VERSION)

include $(BUILD_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/$(PKG_NAME)
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=gpiod implementation in Python
  URL:=https://python-gpiod.github.io/
  DEPENDS:= \
	  +python3-light
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,,\
    install --root="$(PKG_INSTALL_DIR)" --prefix="/usr" --single-version-externally-managed \
	)
endef

define Package/$(PKG_NAME)/description
  A fast and complete Python implementation of gpiod.
endef

define Py3Package/$(PKG_NAME)/filespec
+|$(PYTHON3_PKG_DIR)
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call Py3Package,$(PKG_NAME)))
$(eval $(call BuildPackage,$(PKG_NAME)))
