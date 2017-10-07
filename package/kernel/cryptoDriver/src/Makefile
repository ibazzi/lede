SRC_APP=source
SRC_UTILS=source/utils

obj-m += crypto_k.o
crypto_k-objs:= \
	$(SRC_UTILS)/mtk_sLib.o \
	$(SRC_UTILS)/mtk_arm.o \
	$(SRC_UTILS)/mtk_ringHelper.o \
	$(SRC_UTILS)/mtk_hwDevice.o \
	$(SRC_UTILS)/mtk_hwDmaResource.o \
	$(SRC_UTILS)/mtk_dmaBufHelper.o \
	$(SRC_APP)/mtk_pktProcess.o \
	$(SRC_APP)/mtk_eip93Init.o \
	$(SRC_APP)/mtk_pecInit.o \
	$(SRC_APP)/mtk_interruptHelper.o \
	$(SRC_APP)/mtk_init.o
