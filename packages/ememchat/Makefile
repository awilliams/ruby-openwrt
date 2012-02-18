include $(TOPDIR)/rules.mk

PKG_NAME:=EmEmChat
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME).tar.gz
PKG_SOURCE_URL:=https://github.com/awilliams/EmEmChat/raw/master/build/

include $(INCLUDE_DIR)/package.mk

define Package/EmEmChat
  SECTION:=net
  CATEGORY:=EmEmChat
  DEPENDS:=+ruby +uhttpd +ruby-em-websocket +ruby-json +ruby-core
  TITLE:=EmEmChat server & client
  URL:=https://github.com/awilliams/EmEmChat
endef

define Package/EmEmChat/description
 EmEmChat is a Ruby based chat server using Eventmachine and EmWebocket. The 
 client is a html/javascript application.
endef

define Package/EmEmChat/install
	$(INSTALL_DIR) $(1)/root/EmEmChat
	$(CP) $(PKG_BUILD_DIR)/server/* $(1)/root/EmEmChat/
	$(INSTALL_DIR) $(1)/www
	$(CP) $(PKG_BUILD_DIR)/www/* $(1)/www/
endef

define Build/Compile
endef

$(eval $(call BuildPackage,EmEmChat))
