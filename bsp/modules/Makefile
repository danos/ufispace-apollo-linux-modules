#
# Makefile for kernel test
#
PWD         := $(shell pwd) 
KVERSION    := $(shell uname -r)
KERNEL_DIR   = /lib/modules/$(KVERSION)/build/
KO_DIR   = /lib/modules/$(KVERSION)/extra/

MODULE_NAME  = apollo_cpld.o eeprom_mb.o optoe.o
obj-m       := $(MODULE_NAME)

all:
	make -C $(KERNEL_DIR) M=$(PWD) modules
	mkdir -p ../../target/
	cp *.ko ../../target/
install:
	mkdir -p $(KO_DIR)
	cp *.ko $(KO_DIR)
	depmod -a
clean:
	make -C $(KERNEL_DIR) M=$(PWD) clean
	rm -rf ../../target/*.ko
