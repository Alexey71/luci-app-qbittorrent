#
# Copyright (C) 2017-2020
#
# This is free software, licensed under the GNU General Public License v2.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=qbittorrent
PKG_VERSION:=5.0.0
PKG_RELEASE=2024-08-04

PKG_SOURCE_PROTO:=git
PKG_SOURCE:=qBittorrent-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/qbittorrent/qBittorrent.git
PKG_SOURCE_DATE:=2024-08-04
PKG_SOURCE_VERSION:=66c1acbce25d435ffb815879213a15b20cf3fb2a
PKG_HASH:=e887bba796e1a421b5ff38e40d0d5d5009979d0a6a7204d2e6932b01fcec5e14

PKG_LICENSE:=GPL-2.0+
PKG_LICENSE_FILES:=COPYING
PKG_CPE_ID:=cpe:/a:qbittorrent:qbittorrent

PKG_BUILD_DEPENDS:=qt6tools/host
PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/qbittorrent
	SECTION:=net
	CATEGORY:=Network
	SUBMENU:=BitTorrent
	DEPENDS:=+rblibtorrent +libQt6Core +libQt6Network +libQt6Sql +libQt6Xml +qt6-plugin-libqopensslbackend +qt6-plugin-libqsqlite
	TITLE:=bittorrent client programmed in C++ / Qt
	URL:=https://www.qbittorrent.org/
	PROVIDES:=qBittorrent
endef

define Package/qbittorrent/description
  qBittorrent is a bittorrent client programmed in C++ / Qt that uses
  libtorrent (sometimes called libtorrent-rasterbar) by Arvid Norberg.
  It aims to be a good alternative to all other bittorrent clients out
  there. qBittorrent is fast, stable and provides unicode support as
  well as many features.
endef

CMAKE_OPTIONS += \
	-DCMAKE_BUILD_TYPE=Release \
	-DQT6=ON \
	-DSTACKTRACE=OFF \
	-DWEBUI=ON \
	-DGUI=OFF \
	-DVERBOSE_CONFIGURE=ON \
	-DQT_ADDITIONAL_PACKAGES_PREFIX_PATH=$(STAGING_DIR_HOSTPKG)

define Package/qbittorrent/conffiles
/etc/config/qbittorrent
endef

define Package/qbittorrent/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/qbittorrent-nox $(1)/usr/bin
endef

$(eval $(call BuildPackage,qbittorrent))
