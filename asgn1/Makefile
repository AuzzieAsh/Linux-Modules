MODULE_NAME = asgn1
# EXTRA_CFLAGS += -Werror


obj-m   := $(MODULE_NAME).o


KDIR    := /lib/modules/$(shell uname -r)/build
PWD     := $(shell pwd)



all: module mmap_test

module:
	$(MAKE) -C $(KDIR) M=$(PWD) modules

mmap_test:
	gcc -g -W -Wall mmap_test.c -o mmap_test

clean:
	$(MAKE) -C $(KDIR) M=$(PWD) clean
	rm -f mmap_test mmap_test.o
	rm -f *~
	rm -f output.txt

install: uninstall
	sudo insmod ./asgn1.ko
	sudo chmod 777 /dev/asgn1

uninstall:
	sudo dmesg -c
	-sudo rmmod asgn1

mesg:
	dmesg | grep "asgn1:"
