#
# Makefile for kernel test
#
PWD         := $(shell pwd) 
KVERSION    := $(shell uname -r)
KERNEL_DIR   = /lib/modules/$(KVERSION)/build/
KO_DIR       = /lib/modules/$(KVERSION)/extra/
KO_PCA954X_PATH = /lib/modules/$(KVERSION)/kernel/drivers/i2c/muxes/i2c-mux-pca954x.ko

MODULE_NAME  = x86-64-ufispace-s9700-53dx-cpld.o x86-64-ufispace-s9700-53dx-eeprom-mb.o x86-64-ufispace-s9700-53dx-optoe.o i2c-mux-pca954x.o
obj-m       := $(MODULE_NAME)

all:
	make -C $(KERNEL_DIR) M=$(PWD) modules
	mkdir -p ../../target/
	cp *.ko ../../target/
install:
	mkdir -p $(KO_DIR)
	cp *.ko $(KO_DIR)
	if [ -f "$(KO_PCA954X_PATH)" ]; then rm $(KO_PCA954X_PATH); fi
	depmod -a
clean:
	make -C $(KERNEL_DIR) M=$(PWD) clean
	rm -rf ../../target/*.ko
