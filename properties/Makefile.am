AM_CPPFLAGS = \
	$(GLIB_CFLAGS) \
	$(GTK_CFLAGS) \
	$(NM_CFLAGS) \
	-DICONDIR=\""$(datadir)/pixmaps"\" \
	-DUIDIR=\""$(uidir)"\" \
	-DG_DISABLE_DEPRECATED \
	-DGDK_DISABLE_DEPRECATED \
	-DLOCALEDIR=\"$(datadir)/locale\" \
	-DVERSION=\"$(VERSION)\" \
	-I${top_srcdir}

plugindir = $(libdir)/NetworkManager
plugin_LTLIBRARIES = $(NULL)

sources = nm-openswan.c nm-openswan.h
libs = $(GTK_LIBS) $(NM_LIBS)
ldflags = -avoid-version

if ENABLE_OPENSWAN
plugin_LTLIBRARIES += libnm-openswan-properties.la
libnm_openswan_properties_la_SOURCES = $(sources)
libnm_openswan_properties_la_CPPFLAGS = \
	$(AM_CPPFLAGS) \
	-DDBUS_SERVICE=\"openswan\"
libnm_openswan_properties_la_LIBADD = $(libs)
libnm_openswan_properties_la_LDFLAGS = $(ldflags)
endif

if ENABLE_LIBRESWAN
plugin_LTLIBRARIES += libnm-libreswan-properties.la
libnm_libreswan_properties_la_SOURCES = $(sources)
libnm_libreswan_properties_la_CPPFLAGS = \
	$(AM_CPPFLAGS) \
	-DDBUS_SERVICE=\"libreswan\"
libnm_libreswan_properties_la_LIBADD = $(libs)
libnm_libreswan_properties_la_LDFLAGS = $(ldflags)
endif

uidir = $(datadir)/gnome-vpn-properties/openswan
ui_DATA = nm-openswan-dialog.ui

CLEANFILES = *.bak *~

EXTRA_DIST = $(ui_DATA)
