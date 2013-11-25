#
# Copyright (C) 2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=cpio
PKG_VERSION:=2.10
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@GNU/cpio
PKG_MD5SUM:=edd8d956a5dfb9a3b308fa07f302f691

include $(INCLUDE_DIR)/package.mk

define Package/cpio
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=GNU cpio util
  URL:=http://www.gnu.org/software/cpio/
endef

define Package/cpio/description
 GNU cpio copies files into or out of a cpio or tar archive.
 The archive can be another file on the disk, a magnetic tape, or a pipe.
endef

$(eval $(call BuildPackage,cpio)) 

