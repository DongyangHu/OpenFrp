include $(TOPDIR)/rules.mk


# Custom Values START
FRP_VERSION:=0.57.0
FRP_NAME:=frp
PKG_SOURCE:=$(FRP_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/fatedier/frp/tar.gz/v$(FRP_VERSION)?
PKG_HASH:=460e3ea0aa18c63f21fd5e31663743dedaed2b2f75772050a7627e8534b5f47d
# Custom Values START

PKG_NAME:=luci-app-easy-frpc
PKG_VERSION:=1.0.0
PKG_RELEASE:=1
PKG_BUILD_DIR:=$(BUILD_DIR)/luci-app-easy-frpc-$(PKG_VERSION)
PKG_LICENSE:=Apache License 2.0
PKG_LICENSE_FILESL:=/LICENSE
PKG_MAINTAINER:=https://github.com/DongyangHu/OpenFrp	

PKG_BUILD_DEPENDS:=golang/host
GO_PKG:=https://github.com/fatedier/frp
#GO_PKG_BUILD_PKG:=https://github.com/fatedier/frp/cmd/...
GO_PKG_LDFLAGS:=-s -w


include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk

define Package/luci-app-easy-frpc
  CATEGORY:=LuCI
  SUBMENU:=3. Applications
  TITLE:=All in one for frpc, include Luci and executable file
  DEPENDS:=$$(GO_ARCH_DEPENDS)
  URL:=https://github.com/fatedier/frp
endef

define Package/luci-app-easy-frpc/description
  All in one for frpc, include Luci and executable file.
endef

define Build/Compile
		
endef

define Package/luci-app-easy-frpc/install
	$(call GoPackage/Package/Install/Bin,$(PKG_INSTALL_DIR))
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/$(1) $(1)/usr/bin/
endef

$(eval $(call GoPackage,$(PKG_NAME)))
$(eval $(call BuildPackage,$(PKG_NAME)))