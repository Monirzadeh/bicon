include keymaps.mk

ALL_KEYMAPS_MAP_GZ = $(ALL_KEYMAPS_MAP:=.gz)
ALL_ARABICS_MAP_GZ = $(ALL_ARABICS_MAP:=.gz)

keymapdir = $(pkgdatadir)/keymap
dist_keymap_DATA = $(ALL_KEYMAPS_MAP_GZ)
noinst_DATA = $(ALL_ARABICS_MAP_GZ)

CLEANFILES = *.map.gz

SUFFIXES = .map .map.gz

.map.map.gz:
	gzip --best -c $< > $@

$(ALL_ARABICS_MAP_GZ):
	@$(LN_S) arabic.map.gz $@ \
	&& echo Creating symlink for $@ succeeded \
	|| echo Creating symlink for $@ failed

install-data-hook:
	@cd "$(DESTDIR)$(keymapdir)" && \
	for ter_map_gz in $(ALL_ARABICS_MAP_GZ); do \
		$(LN_S) arabic.map.gz $$ter_map_gz \
		&& echo Creating symlink for $$ter_map_gz succeeded \
		|| echo Creating symlink for $$ter_map_gz failed; \
	done

uninstall-hook:
	@cd "$(DESTDIR)$(keymapdir)" && \
	for ter_map_gz in $(ALL_ARABICS_MAP_GZ); do \
		if test -L $$ter_map_gz; then \
			echo Removing symlink for $$ter_map_gz; \
		fi \
	done

-include $(top_srcdir)/git.mk
