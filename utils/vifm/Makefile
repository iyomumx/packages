include $(TOPDIR)/rules.mk

PKG_NAME:=vifm
PKG_VERSION:=0.7.5
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@SF/vifm
PKG_MD5SUM:=604f43dde5ba56b0aac03486f118f3ec

include $(INCLUDE_DIR)/package.mk

define Package/vifm
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=filemanager
  TITLE:=Manage your files in vim keybindings
  URL:=http://vifm.sourceforge.net/
  DEPENDS:=+libncursesw +libmagic +libpthread
endef

define Package/vifm/description
Vifm is a ncurses based file manager with vi like keybindings, which also borrows some useful ideas from mutt.
If you use vi, vifm gives you complete keyboard control over your files without having to learn a new set of commands.
endef

CONFIGURE_ARGS+=--without-dyn-X11 --without-gtk --without-X11

define Package/vifm/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/vifm $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/vifm-pause $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/vifmrc-converter $(1)/usr/bin/
endef

$(eval $(call BuildPackage,vifm)) 

