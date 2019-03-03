# Drawspaces plugin
plugindir = $(PLUMA_PLUGINS_LIBS_DIR)

INCLUDES = \
	-I$(top_srcdir) 				\
	$(PLUMA_CFLAGS) 				\
	$(WARN_CFLAGS)					\
	$(DISABLE_DEPRECATED_CFLAGS)

plugin_LTLIBRARIES = libdrawspaces.la

libdrawspaces_la_SOURCES = \
	pluma-drawspaces-plugin.h				\
	pluma-drawspaces-plugin.c				

libdrawspaces_la_LDFLAGS = $(PLUGIN_LIBTOOL_FLAGS)
libdrawspaces_la_LIBADD = $(PLUMA_LIBS)

uidir = $(PLUMA_PLUGINS_DATA_DIR)/drawspaces
ui_DATA = drawspaces.ui

# Plugin Info

plugin_in_files = drawspaces.pluma-plugin.desktop.in

%.plugin: %.pluma-plugin.desktop.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*po) ; $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -d -u -c $(top_builddir)/po/.intltool-merge-cache

plugin_DATA = $(plugin_in_files:.pluma-plugin.desktop.in=.plugin)

@INTLTOOL_XML_NOMERGE_RULE@
drawspaces_gschema_in = org.mate.pluma.plugins.drawspaces.gschema.xml.in
gsettings_SCHEMAS = $(drawspaces_gschema_in:.xml.in=.xml)
@GSETTINGS_RULES@

EXTRA_DIST = $(ui_DATA) $(plugin_in_files) $(drawspaces_gschema_in)

CLEANFILES = $(plugin_DATA) $(drawspaces_gschema_in) $(gsettings_SCHEMAS)
DISTCLEANFILES = $(plugin_DATA) $(drawspaces_gschema_in) $(gsettings_SCHEMAS)

-include $(top_srcdir)/git.mk
