#
# Copyright (C) 2007-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=bmon
PKG_VERSION:=3.8
PKG_RELEASE:=2

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/tgraf/bmon/releases/download/v$(PKG_VERSION)/
PKG_MD5SUM:=162ce0d108ff32cbf44b874c5a7e8147
PKG_MAINTAINER:=Baptiste Jonglez <openwrt-pkg@bitsofnetworks.org>
PKG_LICENSE:=MIT

include $(INCLUDE_DIR)/package.mk

define Package/bmon
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+libncursesw +libnl-core +libnl-route +confuse +terminfo
  TITLE:=bmon is a portable bandwidth monitor
  URL:=https://github.com/tgraf/bmon/
endef

define Package/bmon/description
	bmon is a portable bandwidth monitor
	and rate estimator running on various
	operating systems. It supports various
	input methods for different architectures.
endef

CONFIGURE_ARGS += \
	--disable-cnt-workaround \

CONFIGURE_VARS += \
	ac_cv_lib_nl_nl_connect=no \

# Needed to compile some objects
TARGET_CFLAGS+= -std=gnu99

define Package/bmon/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/bmon $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,bmon))
