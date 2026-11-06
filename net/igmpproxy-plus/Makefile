include $(TOPDIR)/rules.mk

PKG_NAME:=igmpproxy-plus
PKG_VERSION:=1.1.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/Alpaca-The-Peacemaker/igmpproxy-plus/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=c07dabcab6cc5040c5847481ea23a63632d19063461680e87d3d1411558e5f54

PKG_MAINTAINER:=Dave Ferreira <8hx8dfdss2@privaterelay.appleid.com>
PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING
PKG_FIXUP:=autoreconf
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/igmpproxy-plus
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Routing and Redirection
  DEPENDS:=+USE_GLIBC:librt
  TITLE:=IGMP proxy with fast leave and timer control
  URL:=https://github.com/Alpaca-The-Peacemaker/igmpproxy-plus
  CONFLICTS:=igmpproxy
endef

define Package/igmpproxy-plus/description
 Alternative to igmpproxy with per interface fast leave (off/on/auto),
 configurable last member query interval and count, querier timers,
 upstream leave delay, exact host tracking and a JSON status socket
 ("igmpproxy -S"). Uses the same /etc/config/igmpproxy as igmpproxy.
endef

define Package/igmpproxy-plus/conffiles
/etc/config/igmpproxy
endef

define Package/igmpproxy-plus/install
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/igmpproxy.config $(1)/etc/config/igmpproxy
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/igmpproxy.init $(1)/etc/init.d/igmpproxy
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/igmpproxy $(1)/usr/sbin/igmpproxy
endef

$(eval $(call BuildPackage,igmpproxy-plus))
