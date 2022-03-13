# KernelMod_LUG
Linux Kernel module that prints Hello Vit upon installation

# Dependencies.
What we need (on Fedora):

   the Package Group “C Development Tools and Libraries”.

   the kernel devel package.

   elfutils.
    
    sudo dnf group install "C Development Tools and Libraries"
    sudo dnf install kernel-devel
    sudo dnf install elfutils-libelf-devel
 
# Building the module:

The Makefile looks like this:

    obj-m += world.o

    all:
	  make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

    clean:
	  make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

to build the module run:

    make
    
to insert/load the module into the kernel:

    insmod world.ko
    
to check if the __init function of the module is called or not:

    dmesg | grep "Hello VIT!"
    
to remove this module from the kernel:
     
     rmmod world
    
to check if __exit function of the module is called or not run:

    dmesg | grep "Why did you just do that?"
    
 
