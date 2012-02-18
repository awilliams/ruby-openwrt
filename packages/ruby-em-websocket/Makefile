include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

RUBY_PKG_LIBVER:=1.9

PKG_NAME:=ruby-em-websocket
PKG_RELEASE:=1
PKG_REV:=master
PKG_VERSION:=$(PKG_REV)

PKG_SOURCE:=$(PKG_NAME).tar.gz
PKG_SOURCE_URL:=git://github.com/awilliams/em-websocket.git
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_PROTO:=git

include $(INCLUDE_DIR)/package.mk

define Package/ruby-em-websocket
  SUBMENU:=Ruby
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Ruby em-websocket gem
  DEPENDS:=+ruby-eventmachine +ruby-enc-utf +ruby-openssl
endef

RUBY:= \
	$(STAGING_DIR_HOST)/bin/ruby -I $(STAGING_DIR_HOST)/share/ri \

define Package/ruby-em-websocket/description
 This package contains the ruby em-websocket gem.
endef

define Build/Compile
	true
endef

define Package/ruby-em-websocket/install
	$(INSTALL_DIR) $(1)/usr/lib/ruby/site_ruby/1.9/
	$(CP) $(PKG_BUILD_DIR)/lib/* $(1)/usr/lib/ruby/site_ruby/1.9/
endef

$(eval $(call BuildPackage,ruby-em-websocket))
