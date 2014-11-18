AM_CPPFLAGS = \
	$(DBUS_CFLAGS) \
	$(GLIB_CFLAGS) \
	$(NM_CFLAGS) \
	$(LIBNL_CFLAGS) \
	-DG_DISABLE_DEPRECATED \
	-DBINDIR=\"$(bindir)\" \
	-DPREFIX=\""$(prefix)"\" \
	-DSYSCONFDIR=\""$(sysconfdir)"\" \
	-DVERSION="\"$(VERSION)\"" \
	-DLIBDIR=\""$(libdir)"\" \
	-DLIBEXECDIR=\""$(libexecdir)"\" \
	-DLOCALSTATEDIR=\""$(localstatedir)"\" \
	-DDATADIR=\"$(datadir)\" \
	-DNM_OPENSWAN_LOCALEDIR=\"$(datadir)/locale\" \
	-I${top_srcdir}

libexec_PROGRAMS = $(NULL)

service_sources = \
	nm-openswan-service.c \
	nm-openswan-service.h
service_ldadd = $(DBUS_LIBS) $(GLIB_LIBS) $(NM_LIBS) -lutil

helper_sources = \
	nm-openswan-service-helper.c \
	nm-openswan-service.h
helper_ldadd = $(DBUS_LIBS) $(NM_LIBS) $(LIBNL_LIBS)

if ENABLE_OPENSWAN
libexec_PROGRAMS += nm-openswan-service
nm_openswan_service_SOURCES = $(service_sources)
nm_openswan_service_CPPFLAGS = \
	$(AM_CPPFLAGS) \
	-DDBUS_SERVICE=\"openswan\"
nm_openswan_service_LDADD = $(service_ldadd)

libexec_PROGRAMS += nm-openswan-service-helper
nm_openswan_service_helper_SOURCES = $(helper_sources)
nm_openswan_service_helper_CPPFLAGS = \
	$(AM_CPPFLAGS) \
	-DDBUS_SERVICE=\"openswan\"
nm_openswan_service_helper_LDADD = $(helper_ldadd)
endif

if ENABLE_LIBRESWAN
libexec_PROGRAMS += nm-libreswan-service
nm_libreswan_service_SOURCES = $(service_sources)
nm_libreswan_service_CPPFLAGS = \
	$(AM_CPPFLAGS) \
	-DDBUS_SERVICE=\"libreswan\"
nm_libreswan_service_LDADD = $(service_ldadd)

libexec_PROGRAMS += nm-libreswan-service-helper
nm_libreswan_service_helper_SOURCES = $(helper_sources)
nm_libreswan_service_helper_CPPFLAGS = \
	$(AM_CPPFLAGS) \
	-DDBUS_SERVICE=\"libreswan\"
nm_libreswan_service_helper_LDADD = $(helper_ldadd)
endif

noinst_PROGRAMS = show-xfrm
show_xfrm_SOURCES = show-xfrm.c
show_xfrm_LDADD = $(LIBNL_LIBS) $(GLIB_LIBS)

CLEANFILES = *~
