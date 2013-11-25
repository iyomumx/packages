include $(TOPDIR)/rules.mk

PKG_NAME:=bvi
PKG_VERSION:=1.4.0alpha
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).src.tar.gz
PKG_SOURCE_URL:=@SF/bvi
PKG_MD5SUM:=ab7c2ce680ad4b7a8104814ebc149955

include $(INCLUDE_DIR)/package.mk

define Package/less/Default
  SECTION:=utils
  CATEGORY:=Utilities
  URL:=http://bvi.sourceforge.net/
endef

define Package/bvi
  $(call Package/less/Default)
  SUBMENU:=Editors
  TITLE:=hex editor based on vi
  DEPENDS:=+libncurses
endef

define Package/bvi/description
The bvi is a display-oriented editor for binary files (hex editor), based on the vi texteditor.
endef

define Package/bmore
  $(call Package/less/Default)
  TITLE:=display binary content like more
  DEPENDS:=+libncurses
endef

define Package/bmore/description
bmore is a filter that displays the contents of a binary file on the terminal, one screenful at a time.
endef

define Package/bvi/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/bvi $(1)/usr/bin/
endef

define Package/bmore/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/bmore $(1)/usr/bin/
endef

$(eval $(call BuildPackage,bvi))
$(eval $(call BuildPackage,bmore))

