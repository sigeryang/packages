#
# Copyright (C) 2022 Siger Yang <siger.yang@outlook.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=luaossl
PKG_VERSION:=v0.10
PKG_RELEASE:=1
PKG_MAINTAINER:=Siger Yang <siger.yang@outlook.com>

PKG_MIRROR_HASH:=98e753afe0751a41829ca4779809521e093385504194be30f6d70b196f176454
PKG_SOURCE_URL:=https://github.com/keplerproject/lua-compat-5.3.git
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE_PROTO:=git

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/lua-compat53
  SUBMENU:=Lua
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Lua-5.3-style APIs for Lua 5.2 and 5.1
  DEPENDS:=+liblua
endef

define Package/lua-compat53/description
 Compatibility module providing Lua-5.3-style APIs for Lua 5.2 and 5.1
endef

TARGET_CFLAGS += $(FPIC) -shared -O2 

define Build/Compile
	$(TARGET_CC) $(TARGET_CFLAGS) $(PKG_BUILD_DIR)/lutf8lib.c -o $(PKG_BUILD_DIR)/compat53/utf8.so
	$(TARGET_CC) $(TARGET_CFLAGS) $(PKG_BUILD_DIR)/lstrlib.c -o $(PKG_BUILD_DIR)/compat53/string.so
	$(TARGET_CC) $(TARGET_CFLAGS) $(PKG_BUILD_DIR)/ltablib.c -o $(PKG_BUILD_DIR)/compat53/table.so
endef

define Build/Install
	# Do nothing
endef

define Package/lua-compat53/install
	$(INSTALL_DIR) $(1)/usr/lib/lua
	$(CP) $(PKG_BUILD_DIR)/compat53 $(1)/usr/lib/lua/
endef

$(eval $(call BuildPackage,lua-compat53))
