#
# Copyright (C) 2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=live
PKG_VERSION:=2013.11.10
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME).$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://www.live555.com/liveMedia/public/
PKG_MD5SUM:=e83be70092053e1aec16c8ce5782c3f9

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/openrtsp
  SECTION:=video
  CATEGORY:=Video Streaming
  TITLE:=live555 streaming libraries and testProgs
  URL:=http://www.live555.com/
  DEPENDS:=+libstdcpp
endef

TARGET_CFLAGS += -I./include

TARGET_CXXFLAGS += -DSOCKLEN_T=socklen_t -D_LARGEFILE_SOURCE=1 \
                   -D_FILE_OFFSET_BITS=64 -DLOCALE_NOT_USED \
                   -fexceptions -Wall -DBSD=1 \
                   -I$(PKG_BUILD_DIR)/UsageEnvironment/include \
                   -I$(PKG_BUILD_DIR)/BasicUsageEnvironment/include \
                   -I$(PKG_BUILD_DIR)/liveMedia/include \
                   -I$(PKG_BUILD_DIR)/groupsock/include

define Build/Configure
	( cd $(PKG_BUILD_DIR); \
		$(SED) 's/@CROSS_COMPILE@/$(TARGET_CROSS)/g' \
		    -e 's/@CFLAGS@//g' \
		    config.OpenWrt; \
		./genMakefiles OpenWrt; \
	)
endef

define Package/openrtsp/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/testProgs/openRTSP $(1)/usr/bin/
endef

$(eval $(call BuildPackage,openrtsp))
