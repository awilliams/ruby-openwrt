include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk


RUBY_PKG_LIBVER:=1.9

PKG_NAME:=ruby-eventmachine
PKG_RELEASE:=1
PKG_REV:=master
PKG_VERSION:=$(PKG_REV)

PKG_SOURCE:=$(PKG_NAME).tar.gz
PKG_SOURCE_URL:=git://github.com/awilliams/eventmachine.git
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_PROTO:=git

include $(INCLUDE_DIR)/package.mk

define Package/ruby-eventmachine
  SUBMENU:=Ruby
  SECTION:=lang
  CATEGORY:=Languages
  DEPENDS:=ruby +libstdcpp +libc +libgcc
  TITLE:=Ruby eventmachine gem
endef

RUBY:= \
	$(STAGING_DIR_HOST)/bin/ruby -I $(STAGING_DIR_HOST)/share/ri \

define Package/ruby-eventmachine/description
 This package contains the ruby eventmachine gem.
endef

define Build/Configure/eventmachine
	(cd $(PKG_BUILD_DIR)/ext; \
		$(RUBY) extconf.rb; \
	);
endef

define Build/Compile/eventmachine
	$(MAKE_VARS) \
	$(MAKE) -C $(PKG_BUILD_DIR)/ext \
		$(MAKE_FLAGS) \
		$(1);
	$(CP) $(PKG_BUILD_DIR)/ext/*.so $(PKG_BUILD_DIR)/lib/
endef

define Build/Configure/fastfilereader
	(cd $(PKG_BUILD_DIR)/ext/fastfilereader; \
		$(RUBY) extconf.rb; \
	);
endef

define Build/Compile/fastfilereader
	$(MAKE_VARS) \
	$(MAKE) -C $(PKG_BUILD_DIR)/ext/fastfilereader \
		$(MAKE_FLAGS) \
		$(1);
	$(CP) $(PKG_BUILD_DIR)/ext/fastfilereader/*.so $(PKG_BUILD_DIR)/lib/
endef

define Build/Configure
	$(call Build/Configure/eventmachine)
	$(call Build/Configure/fastfilereader)
endef

define Build/Compile
	$(call Build/Compile/fastfilereader)
	$(call Build/Compile/eventmachine)
endef

define Package/ruby-eventmachine/install
	$(INSTALL_DIR) $(1)/usr/lib/ruby/site_ruby/1.9/mips-linux
	$(CP) $(PKG_BUILD_DIR)/lib/eventmachine.rb $(1)/usr/lib/ruby/site_ruby/1.9/
	$(CP) $(PKG_BUILD_DIR)/lib/em $(1)/usr/lib/ruby/site_ruby/1.9/
	$(CP) $(PKG_BUILD_DIR)/lib/*.so $(1)/usr/lib/ruby/site_ruby/1.9/mips-linux
endef

$(eval $(call BuildPackage,ruby-eventmachine))
