include $(top_srcdir)/Makefile.common

SUBDIRS = libcommon libkbdfile libkfont libkeymap vlock

PROGS = \
	showkeyonce

bin_PROGRAMS = $(PROGS)

getunimap_CFLAGS = -DUSE_LIBC

spawn_console_SOURCES = spawn_command.c
spawn_login_SOURCES   = spawn_command.c

spawn_console_CFLAGS = -DSPAWN_CONSOLE
spawn_login_CFLAGS   = -DSPAWN_LOGIN

COMMON_LIBS = \
	libcommon/libcommon.a \
	@INTLLIBS@

showkeyonce_LDADD         = $(COMMON_LIBS)

resizecons_LDADD      = libkbdfile/libkbdfile.la $(COMMON_LIBS)

clrunimap_LDADD       = libkfont/libkfont.la $(COMMON_LIBS)
getunimap_LDADD       = libkfont/libkfont.la $(COMMON_LIBS)
loadunimap_LDADD      = libkfont/libkfont.la $(COMMON_LIBS)
mapscrn_LDADD         = libkfont/libkfont.la $(COMMON_LIBS)
psfxtable_LDADD       = libkfont/libkfont.la $(COMMON_LIBS)
setfont_LDADD         = libkfont/libkfont.la $(COMMON_LIBS)
showconsolefont_LDADD = libkfont/libkfont.la $(COMMON_LIBS)

dumpkeys_LDADD        = libkeymap/libkeymap.la libkbdfile/libkbdfile.la $(COMMON_LIBS)
loadkeys_LDADD        = libkeymap/libkeymap.la libkbdfile/libkbdfile.la $(COMMON_LIBS)

install-exec-hook:
	for i in psfaddtable psfgettable psfstriptable; do \
		rm -f $(DESTDIR)$(bindir)/$$i; \
		$(LN_S) psfxtable $(DESTDIR)$(bindir)/$$i || exit $$?; \
	done