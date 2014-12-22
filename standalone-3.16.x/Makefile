ifneq ($(KERNELRELEASE),)
# ugly and dirty hack to avoid patching system's kernel headers
ccflags-y += "-DGREPROTO_NONSTD_EOIP=0x80"
ccflags-y += "-DGREPROTO_NONSTD_MAX=0x81"
ccflags-y += "-DGREPROTO_NONSTD_BASE=0x80"
obj-m  := eoip.o
obj-m  += gre.o
else
KDIR ?= /lib/modules/`uname -r`/build
default:
	@$(MAKE) -C $(KDIR) M=$$PWD
clean:
	@rm -f *.rej *.orig *.o *.ko
	@$(MAKE) -C $(KDIR) M=$$PWD clean
install modules_install:
	@$(MAKE) -C $(KDIR) M=$$PWD modules_install
build:
	@rm -f *.o *.ko
	@$(MAKE) -C $(KDIR) M=$$PWD
endif
