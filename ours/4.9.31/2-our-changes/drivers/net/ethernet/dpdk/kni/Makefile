#
# DPDK KNI module
#

ccflags-y := -Idrivers/net/ethernet/dpdk/kni --param max-inline-insns-single=50 -Wall -Werror
ccflags-$(CONFIG_RTE_KNI_VHOST) += -DRTE_KNI_VHOST
ccflags-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += -Idrivers/net/ethernet/dpdk/kni/ethtool/ixgbe -Idrivers/net/ethernet/dpdk/kni/ethtool/igbe

obj-y += kni_misc.o kni_net.o

obj-$(CONFIG_RTE_KNI_VHOST) += kni_vhost.o

obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += kni_ethtool.o

obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/ixgbe/ixgbe_main.o
obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/ixgbe/ixgbe_api.o
obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/ixgbe/ixgbe_common.o
obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/ixgbe/ixgbe_ethtool.o
obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/ixgbe/ixgbe_82599.o
obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/ixgbe/ixgbe_82598.o
obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/ixgbe/ixgbe_x540.o
obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/ixgbe/ixgbe_phy.o
obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/ixgbe/kcompat.o

obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/igb/e1000_82575.o
obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/igb/e1000_i210.o
obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/igb/e1000_api.o
obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/igb/e1000_mac.o
obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/igb/e1000_manage.o
obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/igb/e1000_mbx.o
obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/igb/e1000_nvm.o
obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/igb/e1000_phy.o
obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/igb/igb_ethtool.o
obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/igb/igb_main.o
obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/igb/igb_param.o
obj-$(CONFIG_RTE_KNI_KMOD_ETHTOOL) += ethtool/igb/igb_vmdq.o
