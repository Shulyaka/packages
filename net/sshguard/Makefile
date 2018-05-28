#
# Copyright (C) 2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=sshguard
PKG_VERSION:=2.1.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=@SF/$(PKG_NAME)
PKG_HASH:=21252a4834ad8408df384ee4ddf468624aa9de9cead5afde1c77380a48cf028a
PKG_MAINTAINER:=Denis Shulyaka <Shulyaka@gmail.com>

TARGET_CFLAGS += -std=gnu99

include $(INCLUDE_DIR)/package.mk

define Package/sshguard
	SECTION:=net
	CATEGORY:=Network
	TITLE:=SSHGuard - blocks brute-force login attempts
	URL:=https://www.sshguard.org/
endef

define Package/sshguard/description
 sshguard protects hosts from brute-force attacks against SSH and other services. It aggregates system logs and blocks repeat offenders using one of several firewall backends, including iptables, ipfw, and pf.
endef

define Package/sshguard/conffiles
	/etc/config/sshguard
endef

define Package/sshguard/install
	$(INSTALL_DIR) $(1)/usr/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/sshguard $(1)/usr/sbin/
	$(INSTALL_DIR) $(1)/usr/lib/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/sshg-logtail $(1)/usr/lib/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/blocker/sshg-blocker $(1)/usr/lib/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/fw/sshg-fw-hosts $(1)/usr/lib/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/fw/sshg-fw-firewalld $(1)/usr/lib/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/fw/sshg-fw-ipfilter $(1)/usr/lib/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/fw/sshg-fw-ipfw $(1)/usr/lib/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/fw/sshg-fw-ipset $(1)/usr/lib/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/fw/sshg-fw-iptables $(1)/usr/lib/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/fw/sshg-fw-nft-sets $(1)/usr/lib/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/fw/sshg-fw-null $(1)/usr/lib/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/fw/sshg-fw-pf $(1)/usr/lib/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/parser/sshg-parser $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/etc/config/
	$(INSTALL_CONF) ./files/sshguard.config $(1)/etc/config/sshguard
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/sshguard.init $(1)/etc/init.d/sshguard
	# Uncomment the below two lines if you're using syslog-ng
	#$(INSTALL_DIR) $(1)/etc/syslog-ng.d/
	#$(INSTALL_BIN) ./files/sshguard.syslog-ng $(1)/etc/syslog-ng.d/sshguard.conf
endef

$(eval $(call BuildPackage,sshguard))
