include $(TOPDIR)/rules.mk

PKG_NAME:=fg360-persistent-logging
PKG_VERSION:=1
PKG_RELEASE:=2
PKGARCH:=all
PKG_LICENSE:=GPL-2.0
PKG_MAINTAINER:=royzheng

include $(INCLUDE_DIR)/package.mk

define Package/fg360-persistent-logging
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Persistent and bounded logging for Arcadyan FG360
  DEPENDS:=+logd +logrotate +syslog-ng
endef

define Package/fg360-persistent-logging/description
 Mounts a bounded persistent /var/log on the validated FG360 user_data
 partition and configures MediaTek AP logging without enabling packet,
 GPS, sensitive, or full modem debug capture.
endef

define Package/fg360-persistent-logging/conffiles
/etc/logrotate.d/fg360-persistent-logging
endef

define Build/Compile
endef

define Package/fg360-persistent-logging/install
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/fg360-persistent-logging.init \
		$(1)/etc/init.d/fg360-persistent-logging

	$(INSTALL_DIR) $(1)/etc/uci-defaults
	$(INSTALL_BIN) ./files/fg360-persistent-logging.defaults \
		$(1)/etc/uci-defaults/95-fg360-persistent-logging

	$(INSTALL_DIR) $(1)/etc/logrotate.d
	$(INSTALL_CONF) ./files/fg360-persistent-logging.logrotate \
		$(1)/etc/logrotate.d/fg360-persistent-logging
endef

$(eval $(call BuildPackage,fg360-persistent-logging))
