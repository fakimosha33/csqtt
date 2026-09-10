include $(TOPDIR)/rules.mk

PKG_NAME:=csqtt-server
PKG_VERSION:=1.0
PKG_RELEASE:=1

PKG_BUILD_DIR := $(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/csqtt-server
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=CSQTT Rust Server for Keenetic
  DEPENDS:=+libstdcpp +libgcc
endef

define Package/csqtt-server/compile
    # Сборка Rust-бинарника под mipsel
    cd $(PKG_BUILD_DIR)/src && \
    cargo build --release --target mipsel-unknown-linux-musl
endef

define Package/csqtt-server/install
    $(INSTALL_DIR) $(1)/opt/csqtt
    $(CP) $(PKG_BUILD_DIR)/src/target/mipsel-unknown-linux-musl/release/csqtt-server $(1)/opt/csqtt/

    $(INSTALL_DIR) $(1)/opt/etc/init.d
    $(INSTALL_BIN) ./files/S99csqtt $(1)/opt/etc/init.d/
endef

$(eval $(call BuildPackage,csqtt-server))
