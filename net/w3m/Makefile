include $(TOPDIR)/rules.mk

PKG_NAME:=w3m
PKG_VERSION:=0.5.3
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=@SF/w3m
PKG_MD5SUM:=1b845a983a50b8dec0169ac48479eacc

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1
PKG_BUILD_DEPENDS:=w3m/host

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk
include $(INCLUDE_DIR)/host-build.mk

define Package/w3m
  SECTION:=net
  CATEGORY:=Network
  TITLE:=A text browser for the World Wide Web.
  URL:=http://w3m.sf.net/
  DEPENDS:=+libgc +libncurses +libopenssl \
           +perl +zlib $(ICONV_DEPENDS)
endef

define Package/w3m/description
  w3m is a text-based web browser as well as a pager like `more' or `less'.
  With w3m you can browse web pages through a terminal emulator window (xterm, rxvt or something like that).
  Moreover, w3m can be used as a text formatting tool which typesets HTML into plain text.
endef

CONFIGURE_ARGS += --with-termlib=ncurses --with-editor=/bin/vi \
                  --enable-image=no --disable-nntp \
                  --disable-w3mmailer --enable-mouse

MAKE_FLAGS += MKTABLE="$(HOST_BUILD_DIR)/mktable"
HOST_MAKE_FLAGS += MKTABLE="./mktable"

define Host/Compile
  $(call Host/Compile/Default,mktable)
endef

define Host/Install
endef

define Package/w3m/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/w3m $(1)/usr/bin/

	$(INSTALL_DIR) $(1)/usr/lib/w3m
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/lib/w3m/{inflate,xface2xpm} $(1)/usr/lib/w3m/

	$(INSTALL_DIR) $(1)/usr/lib/w3m/cgi-bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/lib/w3m/cgi-bin/* $(1)/usr/lib/w3m/cgi-bin/

	$(INSTALL_DIR) $(1)/usr/share/w3m
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/share/w3m/* $(1)/usr/share/w3m/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,w3m))
