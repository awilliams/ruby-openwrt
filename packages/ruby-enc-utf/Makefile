include $(TOPDIR)/rules.mk

PKG_NAME:=ruby-enc-utf
PKG_VERSION:=1.9.2-p0
PKG_RELEASE:=1

PKG_LIBVER:=1.9

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=ftp://ftp.ruby-lang.org/pub/ruby/$(PKG_LIBVER)/
PKG_MD5SUM:=d8a02cadf57d2571cd4250e248ea7e4b

PKG_BUILD_DEPENDS:=ruby/host
PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk

define Package/ruby-enc-utf
  SUBMENU:=Ruby
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Ruby utf* encodings 
  URL:=http://www.ruby-lang.org/
endef

define Package/ruby-enc-utf/description
  Ruby UTF* encodings
endef

define Package/ruby-enc-utf/install
	( cd $(PKG_INSTALL_DIR); $(TAR) -cf - \
		usr/lib/ruby/$(PKG_LIBVER)/*/enc/utf_* \
	) | ( cd $(1); $(TAR) -xf - )
endef

$(eval $(call BuildPackage,ruby-enc-utf))
