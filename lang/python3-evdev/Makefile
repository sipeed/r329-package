#
# Copyright (C) 2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(BUILD_DIR)/kernel.mk

PKG_NAME:=python3-evdev
PKG_VERSION:=1.4.0
PKG_RELEASE:=2

PKG_LICENSE:=BSD-3-Clause
PKG_MAINTAINER:=Paulo Costa <me@paulo.costa.nom.br>, Alexandru Ardelean <ardeleanalex@gmail.com>

PKG_SOURCE:=evdev-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/p/evdev/
PKG_HASH:=b1c649b4fed7252711011da235782b2c260b32e004058d62473471e5cd30634d

PKG_BUILD_DIR:=$(COMPILE_DIR)/evdev-$(PKG_VERSION)

include $(BUILD_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-evdev
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=python3-evdev
  URL:=https://github.com/gvalkov/python-evdev
  DEPENDS:= \
			+libc \
			+libpthread \
      +python3-light \
      +python3-ctypes
endef

define Package/python3-evdev/description
	Bindings to the Linux input handling subsystem
endef

LINUX_EVDEV_HEADERS="$(CONFIG_TOOLCHAIN_ROOT)/include/linux/input.h:$(CONFIG_TOOLCHAIN_ROOT)/include/linux/input-event-codes.h"

define Build/Compile
	$(call Build/Compile/Py3Mod,,\
		install --root="$(PKG_INSTALL_DIR)" --prefix="/usr" \
    build \
    build_ecodes --evdev-headers="$(LINUX_EVDEV_HEADERS)" \
		build_ext \
	)
endef

define Py3Package/python3-evdev/filespec
+|$(PYTHON3_PKG_DIR)
endef

define Package/python3-evdev/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call Py3Package,python3-evdev))
$(eval $(call BuildPackage,python3-evdev))
