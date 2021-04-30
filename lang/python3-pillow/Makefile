#
# Copyright © 1997-2011 by Secret Labs AB
# Copyright © 1995-2011 by Fredrik Lundh
# Copyright © 2016 by Alex Clark and contributors
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-pillow
PKG_VERSION:=8.1.2
PKG_RELEASE:=1

PKG_SOURCE:=Pillow-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/p/pillow/

PKG_MAINTAINER:=Alexandru Ardelean <ardeleanalex@gmail.com>
PKG_LICENSE:=HPND
PKG_LICENSE_FILES:=LICENSE
PKG_CPE_ID:=cpe:/a:python:pillow
PKG_BUILD_DIR:=$(COMPILE_DIR)/Pillow-$(PKG_VERSION)

include $(BUILD_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-pillow
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=The friendly PIL fork
  URL:=https://python-pillow.org/
  DEPENDS:=+libfreetype +libjpeg +zlib +python3
endef

define Package/python3-pillow/description
  The friendly PIL fork
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,,\
		install --root="$(PKG_INSTALL_DIR)" --prefix="/usr" \
		--single-version-externally-managed build_ext \
		--enable-zlib \
		--enable-jpeg \
		--enable-freetype \
		--disable-lcms \
		--disable-webp \
		--disable-webpmux \
		--disable-jpeg2000 \
		--disable-imagequant \
		--disable-platform-guessing\
	)
endef

define Py3Package/python3-pillow/filespec
+|$(PYTHON3_PKG_DIR)
endef

define Package/python3-pillow/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call Py3Package,python3-pillow))
$(eval $(call BuildPackage,python3-pillow))
