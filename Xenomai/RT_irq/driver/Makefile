prefix := $(shell xeno-config --prefix)

ifeq ($(prefix),)
$(error Please add <xenomai-install-path>/bin to your PATH variable)
endif

CC = $(shell xeno-config --cc)
PWD:= $(shell pwd)
# ADEOS/Xenomai compatible kernel sources path
KDIR=$(HOME)/Bureau/LE_TR/exercices/BR/buildroot-2014.02/output/build/linux-rpi-3.2.21

EXTRA_CFLAGS += $(shell xeno-config --skin=posix --cflags)
EXTRA_CFLAGS += $(CFLAGS)

obj-m += rpi_gpio_rtdm.o

all:
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

install:
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules_install
	depmod -a

clean:
	rm -f *~ Module.markers Module.symvers modules.order
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) clean

