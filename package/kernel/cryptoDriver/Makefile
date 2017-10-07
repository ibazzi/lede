#
# Copyright (C) 2006-2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=cryptoDriver
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define KernelPackage/cryptoDriver
  SUBMENU:=Network Support
  TITLE:=IPsec HW Crypto Engine
  KCONFIG:=CONFIG_RALINK_HWCRYPTO=m CONFIG_RALINK_HWCRYPTO_ESP6=y
  FILES:=$(PKG_BUILD_DIR)/crypto_k.ko
  AUTOLOAD:=$(call AutoLoad,60,crypto_k)
endef

define KernelPackage/cryptoDriver/description
 Kernel module to enable IPsec HW Crypto Engine.
endef

# Include Paths
INCLUDE_FLAGS_ALL:= -I$(PKG_BUILD_DIR)/include
# Compiler Flags
WARNING_FLAGS=-Wno-error=date-time
DEBUG_FLAGS=-g
CODE_COVERAGE_FLAGS=
PROFILING_FLAGS=
BACKWARD_COMPATIBILITY_FLAGS=

EXTRA_CFLAGS += $(BACKWARD_COMPATIBILITY_FLAGS)
EXTRA_CFLAGS += ${INCLUDE_FLAGS_ALL}
EXTRA_CFLAGS += $(WARNING_FLAGS)
EXTRA_CFLAGS += $(DEBUG_FLAGS)
EXTRA_CFLAGS += $(CODE_COVERAGE_FLAGS)
EXTRA_CFLAGS += $(PROFILING_FLAGS)
EXTRA_CFLAGS += -DRT_EIP93_DRIVER
EXTRA_CFLAGS += -DRT_EIP93_DRIVER_DEBUG -DRT_EIP93_DRIVER_DEBUG_H
EXTRA_CFLAGS += -DMTK_CRYPTO_DRIVER
#EXTRA_CFLAGS += -I$(MODULES_KPROFILE_DIR)
#EXTRA_CFLAGS += -DEXPORT_SYMTAB -D__KERNEL_SYSCALLS__

ifeq ($(CONFIG_RA_NETWORK_WORKQUEUE_BH),y)
EXTRA_CFLAGS   += -DWORKQUEUE_BH
endif

MAKE_OPTS:= \
		ARCH="$(LINUX_KARCH)" \
		CROSS_COMPILE="$(TARGET_CROSS)" \
		SUBDIRS="$(PKG_BUILD_DIR)" \
		EXTRA_CFLAGS="$(EXTRA_CFLAGS)"

define Build/Compile
	$(MAKE) -C "$(LINUX_DIR)" \
		$(MAKE_OPTS) \
		modules
endef

$(eval $(call KernelPackage,cryptoDriver))
