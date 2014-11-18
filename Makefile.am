AUTOMAKE_OPTIONS = foreign

SUBDIRS = src

if WITH_GNOME
SUBDIRS += auth-dialog properties po
endif

dbusservicedir = $(sysconfdir)/dbus-1/system.d
dbusservice_DATA = $(NULL)

nmvpnservicedir = $(sysconfdir)/NetworkManager/VPN
nmvpnservice_DATA = $(NULL)

desktopfiles = $(NULL)
namefiles = $(NULL)

if ENABLE_OPENSWAN
dbusservice_DATA += nm-openswan-service.conf
nmvpnservice_DATA += nm-openswan-service.name
desktopfiles += nm-openswan.desktop.in
namefiles += nm-openswan-service.name.in

nm-openswan-service.name: $(srcdir)/nm-openswan-service.name.in
	sed -e 's|[@]LIBEXECDIR[@]|$(libexecdir)|g' \
	    -e 's|[@]PLUGINDIR[@]|$(libdir)/NetworkManager|g' \
	    $< >$@
endif

if ENABLE_LIBRESWAN
dbusservice_DATA += nm-libreswan-service.conf
nmvpnservice_DATA += nm-libreswan-service.name
desktopfiles += nm-libreswan.desktop.in
namefiles += nm-libreswan-service.name.in

nm-libreswan-service.name: $(srcdir)/nm-libreswan-service.name.in
	sed -e 's|[@]LIBEXECDIR[@]|$(libexecdir)|g' \
	    -e 's|[@]PLUGINDIR[@]|$(libdir)/NetworkManager|g' \
	    $< >$@
endif

DISTCHECK_CONFIGURE_FLAGS = --enable-more-warnings=yes

EXTRA_DIST = $(namefiles) \
             $(dbusservice_DATA)  \
             $(desktopfiles)  \
             intltool-extract.in  \
             intltool-merge.in    \
             intltool-update.in \
             nm-test-helpers.h

CLEANFILES = $(nmvpnservice_DATA) $(desktop_DATA) *~
DISTCLEANFILES = intltool-extract intltool-merge intltool-update

ACLOCAL_AMFLAGS = -I m4
