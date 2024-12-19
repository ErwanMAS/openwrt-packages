#
# Copyright (C) 2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=jq
PKG_VERSION:=1.7.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/jqlang/jq/releases/download/$(PKG_NAME)-$(PKG_VERSION)
PKG_HASH:=478c9ca129fd2e3443fe27314b455e211e0d8c60bc8ff7df703873deeee580c2

PKG_MAINTAINER:=Marko Ratkaj <markoratkaj@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING
PKG_CPE_ID:=cpe:/a:jqlang:jq

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/jq/default
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Lightweight and flexible command-line JSON processor.
  URL:=https://jqlang.github.io/jq/
  VARIANT:=$(1)
endef

Package/jq=$(call Package/jq/default,)
Package/jq-full=$(call Package/jq/default,-full)

CONFIGURE_ARGS+= \
	--disable-docs \
	--disable-valgrind

ifeq ($(BUILD_VARIANT),-full)
  CONFIGURE_ARGS+= --without-oniguruma
endif

define Package/jq$(BUILD_VARIANT)/description
	Lightweight and flexible command-line JSON processor.
endef

define Package/jq$(BUILD_VARIANT)/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
endef

$(eval $(call BuildPackage,jq))
$(eval $(call BuildPackage,jq-full))
