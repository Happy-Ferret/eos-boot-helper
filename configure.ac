AC_INIT([eos-boot-helper], [0.0])

AM_INIT_AUTOMAKE([foreign])
AC_CONFIG_SRCDIR([eos-firstboot])
PKG_PROG_PKG_CONFIG

dnl Get systemd unit and udev rules directories. Add options so that they
dnl can be set under $prefix for distcheck.
m4_define([no_systemd_error],
          [m4_normalize([Could not get systemdsystemunitdir setting from]
                        [systemd pkg-config file])])
m4_define([no_udev_error],
          [m4_normalize([Could not get udevdir setting from udev]
                        [pkg-config file])])
AC_ARG_WITH([systemdunitdir],
            [AS_HELP_STRING([--with-systemdunitdir],
                            [Path to the system directory for systemd units])],
            [systemdunitdir="$withval"],
            [PKG_CHECK_VAR([systemdunitdir], [systemd],
                           [systemdsystemunitdir], [],
                           [AC_MSG_ERROR(no_systemd_error)])])
AC_ARG_WITH([udevdir],
            [AS_HELP_STRING([--with-udevdir],
                            [Path to the system udev directory])],
            [udevdir="$withval"],
            [PKG_CHECK_VAR([udevdir], [udev],
                           [udevdir], [],
                           [AC_MSG_ERROR(no_udev_error)])])

AC_CONFIG_FILES([
	Makefile
	dracut/Makefile
	dracut/image-boot/Makefile
	dracut/repartition/Makefile])
AC_OUTPUT
