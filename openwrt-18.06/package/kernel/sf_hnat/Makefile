include $(TOPDIR)/rules.mk

PKG_NAME:=sf_hnat
PKG_RELEASE:=1

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk


define KernelPackage/sf_hnat
  SUBMENU:=Network Devices
  TITLE:=Siflower SFA28 hnat support
  FILES:=$(PKG_BUILD_DIR)/sfhnat.ko
  AUTOLOAD:=$(call AutoLoad,54,sfhnat,1)
  KCONFIG:=
endef

define KernelPackage/sf_hnat/config
	if PACKAGE_kmod-sf_hnat
		config SFAX8_HNAT_TEST_TOOL
			bool "set test tool"
			default "n"
	endif
endef

EXTRA_KCONFIG:= \
	CONFIG_NET_VENDOR_SIFLOWER=y \
	CONFIG_SFAX8_HNAT=m \

ifdef CONFIG_SFAX8_HNAT_TEST_TOOL
EXTRA_KCONFIG += CONFIG_SFAX8_HNAT_TEST_TOOL=y
NOSTDINC_FLAGS += -DCONFIG_SFAX8_HNAT_TEST_TOOL
endif

ifdef CONFIG_TARGET_siflower_sf19a28_mpw1
NOSTDINC_FLAGS += -DCONFIG_SF19A28_MPW1
endif

ifdef CONFIG_TARGET_siflower_sf19a28_fullmask
NOSTDINC_FLAGS += -DCONFIG_SF19A28_FULLMASK
endif


define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./* $(PKG_BUILD_DIR)/
endef

define Build/Compile
endef

$(eval $(call KernelPackage,sf_hnat))
