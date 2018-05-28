#
# Copyright (C) 2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=onioncat
PKG_VERSION:=0.2.1
PKG_RELEASE:=1
PKG_REV:=1b9d955dd575312ece3f9da551ad76733c876471

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/rahra/onioncat.git
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_MAINTAINER:=Denis Shulyaka <Shulyaka@gmail.com>

include $(INCLUDE_DIR)/package.mk

define Package/onioncat
	SECTION:=net
	CATEGORY:=Network
	DEPENDS:=+i2pd
	DEPENDS:=+tor
	TITLE:=OnionCat is a peer-to-peer layer 3 VPN which is based on Tor or I2P
	URL:=https://www.onioncat.org/
endef

define Package/onioncat/description
 OnionCat is a peer-to-peer layer 3 VPN which is based on Tor or I2P. Thus, it offers typical VPN functionality with the addition of location-based anonymity.
endef

define Package/onioncat/conffiles
/etc/ocat.conf
/etc/gcat.conf
endef

TARGET_CFLAGS += -D_PATH_HOSTS="\\\"/etc/hosts\\\""

define Package/onioncat/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/ocat $(1)/usr/bin/
	ln -s -f ocat $(1)/usr/bin/gcat
endef

$(eval $(call BuildPackage,onioncat))
