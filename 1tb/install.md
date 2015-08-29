

Copied from
[OpenStack via DevStack](http://wiki.xen.org/wiki/OpenStack_via_DevStack):

To run Ubuntu/Xubuntu in a complete non-gui mode run:

	sudo service lightdm stop

or install Ubuntu Server Edition which does not has a display manager,
X server etc. Another method is to replace `quiet splash` in grub menu
with `text` in the line starting with `linux`.

If you are using Network Manager to control your internet connections,
then you must first disable it as we will be manually configuring the
connections. Please note that you are about to temporarily lose your
internet connection so it''s important that you are physically connected
to the machine:

	sudo stop network-manager
	echo "manual" | sudo tee /etc/init/network-manager.override

Configure Static IP On Ubuntu (using bridge-utils):

	vi /etc/network/interfaces
	[...]
	auto eth0
	iface eth0 inet manual
	
	auto xenbr0
	iface xenbr0 inet static
	  bridge_ports eth0
	  address 192.168.0.222
	  netmask 255.255.255.0
	  broadcast 192.168.0.255
	  gateway 192.168.0.1
	  dns-nameservers 192.168.0.1 8.8.8.8
	[...]



	apt-get install xen-hypervisor-4.4-amd64
	apt-get install git
	sudo reboot

Get devstack:

	git clone https://git.openstack.org/openstack-dev/devstack
	cd devstack/
	cp doc/source/configuration.rst local.conf
	vi local.conf

Edit local.conf in the devstack working repository:

	[[local|localrc]]
	ADMIN_PASSWORD=secrete
	DATABASE_PASSWORD=$ADMIN_PASSWORD
	RABBIT_PASSWORD=$ADMIN_PASSWORD
	SERVICE_PASSWORD=$ADMIN_PASSWORD
	SERVICE_TOKEN=a682f596-76f3-11e3-b3b2-e716f9080d50
	
	# Useful logging options for debugging:
	DEST=/opt/stack
	LOGFILE=$DEST/logs/stack.sh.log
	SCREEN_LOGDIR=$DEST/logs/screen
	
	# This is a Xen Project host:
	LIBVIRT_TYPE=xen

Run devstack:

	./stack.sh

