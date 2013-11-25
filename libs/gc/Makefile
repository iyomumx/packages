include $(TOPDIR)/rules.mk

PKG_NAME:=gc
PKG_VERSION:=7.2d
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://www.hpl.hp.com/personal/Hans_Boehm/gc/gc_source/
PKG_MD5SUM:=91340b28c61753a789eb6077675d87d2

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libgc
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+libpthread
  TITLE:=C/C++ GC library
  URL:=http://www.hpl.hp.com/personal/Hans_Boehm/gc/‎
endef

define Package/libgc/description
 Library to use GC in C/C++.
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/gc.h $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/include/gc
	$(CP) $(PKG_INSTALL_DIR)/usr/include/gc/*.h $(1)/usr/include/gc/

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/lib{gc,cord}.{la,a,so*} $(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/bdw-gc.pc $(1)/usr/lib/pkgconfig/
endef

define Package/libgc/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/lib{gc,cord}.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libgc))
