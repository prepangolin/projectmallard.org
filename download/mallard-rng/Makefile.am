mal10dir = $(rngdir)/1.0
mal10_DATA = 1.0/mallard-1.0.rnc 1.0/mallard-1.0.rng

if10dir = $(rngdir)/if/1.0
if10_DATA = if/1.0/if-1.0.rnc if/1.0/if-1.0.rng

catalogdir = $(sysconfdir)/xml/mallard
catalog_DATA = catalog

EXTRA_DIST =			\
	$(mal10_DATA)		\
	$(if10_DATA)		\
	catalog.in

install-exec-hook:
	test -n "$(DESTDIR)" || ( \
	cd $(sysconfdir)/xml; \
	test -f catalog && xmlcatalog --noout --del file://$(sysconfdir)/xml/mallard/catalog catalog >/dev/null; \
	test -e catalog || xmlcatalog --noout --create catalog; \
	xmlcatalog --noout --add nextCatalog file://$(sysconfdir)/xml/mallard/catalog "" catalog >/dev/null; \
	)

uninstall-hook:
	test -n "$(DESTDIR)" || ( \
	cd $(sysconfdir)/xml; \
	xmlcatalog --noout --del file://$(sysconfdir)/xml/mallard/catalog catalog >/dev/null; \
	test -s catalog || rm -f catalog; \
	)
