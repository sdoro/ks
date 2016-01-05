
### how to transfer an ISO image into USB or CF


Nowdays the procedure is very simple. Suppose that the output
device is named sdX (without partition):

    dd if=file.iso of=/dev/sdX bs=64k

Proved Fedora iso file both with USB that with CF.

