#
# Copyright (C) 2015-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-pyasn1-modules
PKG_VERSION:=0.2.5
PKG_RELEASE:=1

PKG_SOURCE:=pyasn1-modules-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/source/p/pyasn1-modules
PKG_HASH:=ef721f68f7951fab9b0404d42590f479e30d9005daccb1699b0a51bb4177db96

PKG_LICENSE:=BSD-2-Clause
PKG_LICENSE_FILES:=LICENSE.txt
PKG_MAINTAINER:=Jeffery To <jeffery.to@gmail.com>, Alexandru Ardelean <ardeleanalex@gmail.com>

PKG_BUILD_DIR:=$(BUILD_DIR)/$(BUILD_VARIANT)-pyasn1-modules-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/python-pyasn1-modules/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Collection of ASN.1 modules
  URL:=https://github.com/etingof/pyasn1-modules
endef

define Package/python-pyasn1-modules
$(call Package/python-pyasn1-modules/Default)
  DEPENDS:= \
      +PACKAGE_python-pyasn1-modules:python-light \
      +PACKAGE_python-pyasn1-modules:python-pyasn1
  VARIANT:=python
endef

define Package/python3-pyasn1-modules
$(call Package/python-pyasn1-modules/Default)
  DEPENDS:= \
      +PACKAGE_python3-pyasn1-modules:python3-light \
      +PACKAGE_python3-pyasn1-modules:python3-pyasn1
  VARIANT:=python3
endef

define Package/python-pyasn1-modules/description
This is a small but growing collection of ASN.1 data structures
expressed in Python terms using pyasn1 data model.
endef

define Package/python3-pyasn1-modules/description
$(call Package/python-pyasn1-modules/description)
.
(Variant for Python3).
endef

$(eval $(call PyPackage,python-pyasn1-modules))
$(eval $(call BuildPackage,python-pyasn1-modules))
$(eval $(call BuildPackage,python-pyasn1-modules-src))

$(eval $(call Py3Package,python3-pyasn1-modules))
$(eval $(call BuildPackage,python3-pyasn1-modules))
$(eval $(call BuildPackage,python3-pyasn1-modules-src))
