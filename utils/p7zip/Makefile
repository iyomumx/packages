# 
# Copyright (C) 2006-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=p7zip
PKG_VERSION:=9.20.1
PKG_RELEASE:=3

PKG_SOURCE:=$(PKG_NAME)_$(PKG_VERSION)_src_all.tar.bz2
PKG_SOURCE_URL:=@SF/p7zip
#PKG_MD5SUM:=

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)_$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/p7zip
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=compression
  TITLE:=7-Zip
  DEPENDS:=+libpthread +libstdcpp
  MAINTAINER:=QQ 810091899
  URL:= http://p7zip.sf.net
endef

define Package/p7zip/description
 7-Zip is a file archiver with highest compression ratio.
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		CXX="$(TARGET_CXX) -Os -pipe -s -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -DNDEBUG -D_REENTRANT -DENV_UNIX -D_7ZIP_LARGE_PAGES -DBREAK_HANDLER -DUNICODE -D_UNICODE -fPIC" \
		CC="$(TARGET_CC) -Os -pipe -s -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -DNDEBUG -D_REENTRANT -DENV_UNIX -D_7ZIP_LARGE_PAGES -DBREAK_HANDLER -DUNICODE -D_UNICODE -fPIC" \
		CPPFLAGS="-c -I. -I../../../../C -I../../../myWindows -I../../../include_windows -I../../.. -I../../C " \
		CXXFLAGS="-c -I. -I../../../../C -I../../../myWindows -I../../../include_windows -I../../.. -I../../C " \
		LIBS="-lpthread -ldl" \
		7za
endef
	
define Package/p7zip/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/bin/7za $(1)/usr/bin/7z
endef

$(eval $(call BuildPackage,p7zip))
