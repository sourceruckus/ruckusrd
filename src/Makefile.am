dist_bin_SCRIPTS =
dist_bin_SCRIPTS += ruckusrd

dist_sysconf_DATA =
dist_sysconf_DATA += ruckusrd.conf

pkgdata_DATA =
pkgdata_DATA += firstboot_wizard
pkgdata_DATA += linuxrc
pkgdata_DATA += mount_sysroot
pkgdata_DATA += ruckusrd.sh
pkgdata_DATA += ruckusrd-common.sh
pkgdata_DATA += system_installer
pkgdata_DATA += umount_sysroot
pkgdata_DATA += initramfs.cpio.xz


install-exec-hook:
	rm -f $(DESTDIR)$(bindir)/mkinitrd
	(cd $(DESTDIR)$(bindir) && $(LN_S) ruckusrd mkinitrd)
	sed -i 's|__LIBDIR__|$(pkgdatadir)|' $(DESTDIR)$(bindir)/ruckusrd
	sed -i 's|__CONFDIR__|$(sysconfdir)|' $(DESTDIR)$(bindir)/ruckusrd

uninstall-local:
	rm -f $(DESTDIR)$(bindir)/mkinitrd

initramfs.cpio.xz: ../Makefile ruckusrd.prep linuxrc mount_sysroot umount_sysroot system_installer firstboot_wizard ruckusrd.sh ruckusrd-common.sh ../subprojects/busybox.tar ../subprojects/util-linux.tar ../subprojects/eudev.tar ../subprojects/mdadm.tar ../subprojects/lvm2.tar ../subprojects/e2fsprogs.tar ../subprojects/squashfs-tools.tar ../subprojects/zfs.tar ../subprojects/syslinux.tar ../subprojects/dropbear.tar ../subprojects/rsync.tar ../subprojects/efibootmgr.tar ../subprojects/groff.tar ../subprojects/zstd.tar ../subprojects/less.tar
	./ruckusrd.prep


clean-local:
	rm -f initramfs.cpio.xz
	rm -rf initramfs
