include $(TOPDIR)/rules.mk
include $(TOPDIR)/rules.mk

LUCI_TITLE:=LuCI example app for js based luci
LUCI_DEPENDS:=+luci-base
LUCI_PKGARCH:=all

include ../../luci.mk

# Custom Values START
FRP_VERSION:=0.57.0
FRP_NAME:=frp
FRP_SUB_NAME:=frpc
PKG_SOURCE:=$(FRP_NAME)-$(FRP_VERSION).tar.gz
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
GO_PKG:=github.com/fatedier/frp
GO_PKG_BUILD_PKG:=github.com/fatedier/frp/cmd/...
#GO_PKG_LDFLAGS:=-s -w


include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk

define Package/luci-app-easy-frpc
  CATEGORY:=LuCI
  SUBMENU:=3. Applications
  TITLE:=All in one for $(FRP_SUB_NAME), include Luci and executable file
  DEPENDS:=$(GO_ARCH_DEPENDS)
  URL:=https://github.com/fatedier/frp
endef

define Package/luci-app-easy-frpc/description
  All in one for $(FRP_SUB_NAME), include Luci and executable file.
endef

define Build/Prepare
  $(Build/Prepare/Default)\
  $(CP) $(BUILD_DIR)/$(FRP_NAME)-$(FRP_VERSION)/* $(PKG_BUILD_DIR)/
endef

define Package/luci-app-easy-frpc/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(GO_PKG_BUILD_BIN_DIR)/$(FRP_SUB_NAME) $(1)/usr/bin/

endef

$(eval $(call BuildPackage,$(PKG_NAME)))