# 
# Copyright (C) 2009 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libcrypto++
PKG_VERSION:=5.6.2

#PKG_SOURCE:=$(PKG_NAME)_$(PKG_VERSION).orig.tar.gz
#PKG_SOURCE_URL:=http://ftp.de.debian.org/debian/pool/main/libc/libcrypto++/
PKG_SOURCE:=cryptopp562.zip
PKG_SOURCE_URL:=http://www.cryptopp.com/
PKG_MD5SUM:=

include $(INCLUDE_DIR)/package.mk

define Package/libcryptoxx
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+libpthread +libstdcpp
  TITLE:=Crypto++ is library for creating C++ programs which use cryptographic algorithms
  URL:=http://packages.debian.org/sid/libcrypto++-dev
endef

define Package/package/libcryptoxx
  Crypto++ is library for creating C++ programs which use cryptographic algorithms.
  The library uses a Pipes & Filters architecture with heavy use of templates and
  abstract base classes.
endef

UNPACK_CMD=unzip -d $(1)/ $(DL_DIR)/$(PKG_SOURCE)

CONFIGURE_ARGS += \
	--enable-static \
	--enable-shared

define Build/Configure
	(cd $(PKG_BUILD_DIR); rm -f config.cache GNUmakefile; autoreconf --force --install)
	$(call Build/Configure/Default,,\
		LDFLAGS="$(TARGET_LDFLAGS) -lpthread" \
	)
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		DESTDIR="$(PKG_INSTALL_DIR)" \
		all install
endef


define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/crypto++
	$(CP) $(PKG_INSTALL_DIR)/usr/include/crypto--/* $(1)/usr/include/crypto++/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libcrypto++.{a,so*} $(1)/usr/lib/
endef

define Package/libcryptoxx/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libcrypto++.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libcryptoxx))
