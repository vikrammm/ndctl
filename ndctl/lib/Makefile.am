include $(top_srcdir)/Makefile.am.in

%.pc: %.pc.in Makefile
	$(SED_PROCESS)

pkginclude_HEADERS = ../libndctl.h
lib_LTLIBRARIES = libndctl.la

libndctl_la_SOURCES =\
	libndctl.h \
	private.h \
	../../util/log.c \
	../../util/log.h \
	../../util/sysfs.c \
	../../util/sysfs.h \
	dimm.c \
	inject.c \
	nfit.c \
	smart.c \
	intel.c \
	hpe1.c \
	msft.c \
	ars.c \
	firmware.c \
	libndctl.c

libndctl_la_LIBADD =\
	../../daxctl/lib/libdaxctl.la \
	$(UDEV_LIBS) \
	$(UUID_LIBS) \
	$(KMOD_LIBS)

EXTRA_DIST += libndctl.sym

libndctl_la_LDFLAGS = $(AM_LDFLAGS) \
	-version-info $(LIBNDCTL_CURRENT):$(LIBNDCTL_REVISION):$(LIBNDCTL_AGE) \
	-Wl,--version-script=$(top_srcdir)/ndctl/lib/libndctl.sym
libndctl_la_DEPENDENCIES = libndctl.sym

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA = libndctl.pc
EXTRA_DIST += libndctl.pc.in
CLEANFILES += libndctl.pc
