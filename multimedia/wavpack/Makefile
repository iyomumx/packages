#
# Copyright (C) 2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=wavpack
PKG_VERSION:=4.70.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=http://www.wavpack.com
PKG_MD5SUM:=4c0186ef0dc8367ce5cd7cc0f398b714

PKG_FIXUP:=autoreconf libtool
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk

define Package/wavpack/Default
  SECTION:=multimedia
  CATEGORY:=Multimedia
  TITLE:=WavPack
  DEPENDS:= $(ICONV_DEPENDS)
  URL:=http://www.wavpack.com/
endef

define Package/libwavpack
$(call Package/wavpack/Default)
  TITLE+= library
endef

define Package/libwavpack/description
WavPack is a completely open audio compression format providing lossless, high-quality lossy, and a unique hybrid compression mode.
This package includes library for wavpack.
endef

define Package/wavpack
$(call Package/wavpack/Default)
  TITLE+= program
  DEPENDS+= +libwavpack
endef

define Package/wavpack/description
WavPack is a completely open audio compression format providing lossless, high-quality lossy, and a unique hybrid compression mode.
This package includes programs for wavpack.
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libwavpack.{a,la,so*} $(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/wavpack.pc $(1)/usr/lib/pkgconfig/

	$(INSTALL_DIR) $(1)/usr/include/wavpack
	$(CP) $(PKG_INSTALL_DIR)/usr/include/wavpack/wavpack.h $(1)/usr/include/wavpack/
endef

define Package/libwavpack/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libwavpack.so* $(1)/usr/lib/
endef

define Package/wavpack/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/{wavpack,wvgain,wvunpack} $(1)/usr/bin/
endef

$(eval $(call BuildPackage,libwavpack))
$(eval $(call BuildPackage,wavpack))
