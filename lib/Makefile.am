lib_LTLIBRARIES = \
	libgnome-pomodoro.la

noinst_HEADERS = gnome-pomodoro.h

libgnome_pomodoro_la_VALASOURCES = \
	animation.vala \
	about-dialog.vala \
	accelerator.vala \
	application.vala \
	capability.vala \
	capability-group.vala \
	desktop.vala \
	log-scale.vala \
	preferences-dialog.vala \
	presence.vala \
	screen-notification.vala \
	service.vala \
	settings.vala \
	timer.vala \
	timer-state.vala \
	utils.vala \
	window.vala

libgnome_pomodoro_la_SOURCES = \
	$(libgnome_pomodoro_la_VALASOURCES) \
	resources.c

libgnome_pomodoro_la_VALAFLAGS = \
	$(GNOME_POMODORO_VALAFLAGS) \
	--library=gnome-pomodoro \
	--header=gnome-pomodoro.h \
	--vapi=gnome-pomodoro.vapi \
	--gresources $(top_srcdir)/lib/resources/resources.xml

libgnome_pomodoro_la_CPPFLAGS = \
	$(GNOME_POMODORO_CPPFLAGS) \
	-DGETTEXT_PACKAGE=\"$(GETTEXT_PACKAGE)\" \
	-DPACKAGE_LOCALE_DIR=\""$(localedir)\"" \
	-DPACKAGE_DATA_DIR=\""$(pkgdatadir)\""

libgnome_pomodoro_la_CFLAGS = \
	$(GNOME_POMODORO_CFLAGS) \
	$(WARNING_CFLAGS)

libgnome_pomodoro_la_LIBADD = \
	$(GNOME_POMODORO_LIBS)

resources = \
	resources/resources.xml
resources_deps = \
	$(shell $(GLIB_COMPILE_RESOURCES) --generate-dependencies --sourcedir=resources $(resources))

resources.c: $(resources) $(resources_deps)
	$(AM_V_GEN) $(GLIB_COMPILE_RESOURCES) --generate-source --c-name="pomodoro" --sourcedir=resources --target=$@ $<

BUILT_SOURCES = \
	resources.c

CLEANFILES = \
	$(BUILT_SOURCES) \
	$(libgnome_pomodoro_la_SOURCES:.vala=.c) \
	gnome-pomodoro.h \
	gnome-pomodoro.vapi \
	libgnome-pomodoro.la \
	libgnome_pomodoro_la_vala.stamp

EXTRA_DIST = \
	$(resources) \
	$(resources_deps)

-include $(top_srcdir)/git.mk

# vi:ts=4:noet
