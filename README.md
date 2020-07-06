# chrootctl
Odroid go advance chroot and QEMU user emulation

This small script can be used to create a chroot environment with a
QEMU user emulation attached.

The script can download the last official Ubuntu ES image for the
Odroid, and extract from it the rootfs. If QEMU is installed in the
system, it will register (binfmt) the appropriate loaders for the
ARM[64] binaries. This will allows the execution of ARM application
transparently inside the chroot environment.

Example:

```bash
# Download the last image
./chrootctl fetch

# Extract the rootfs and create the chroot
./chrootctl create

# Register the loaders and enter the chroot
./chrootctl shell

# Now we can update the system and install the compilers
apt update && apt upgrade && apt install build-essential

# Exit the chroot and umount the binds
exit

# Show other options
./chrootctl -h
```
