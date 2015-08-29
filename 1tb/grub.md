
For testing OpenStack I choose to use a portable hard disk and
loaded different OS with different hypervisors and different OpenStack
release.

To maintain the grub menu I suggest to boot in Xen distribution
and then lunch:

	update-grub

entually run:

	grub-install /dev/sda

Actually [screenshot](https://github.com/sdoro2/openStack/blob/master/U-LTS-Xen/screenshot/grub.png). Thanks to `apt-get install grub-emu`.

