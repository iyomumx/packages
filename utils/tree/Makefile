include $(TOPDIR)/rules.mk

PKG_NAME:=tree
PKG_VERSION:=1.6.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tgz
PKG_SOURCE_URL:=ftp://mama.indstate.edu/linux/tree/
PKG_MD5SUM:=04e967a3f4108d50cde3b4b0e89e970a

include $(INCLUDE_DIR)/package.mk

define Package/tree
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=List your files in tree view
  URL:=http://mama.indstate.edu/users/ice/tree/
  DEPENDS:=
endef

define Package/tree/description
Tree is a recursive directory listing command that produces a depth indented listing of files,
which is colorized ala dircolors if the LS_COLORS environment variable is set and output is to tty.
endef

define Build/Configure
endef

define Package/tree/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/tree $(1)/usr/bin/
endef

$(eval $(call BuildPackage,tree)) 

