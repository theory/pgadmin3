##############################################################################
# pgAdmin III - PostgreSQL Tools
# 
# Copyright (C) 2002 - 2009, The pgAdmin Development Team
# This software is released under the PostgreSQL Licence
#
# Makefile - Makefile for *nix systems
##############################################################################

EXTRA_DIST = \
	$(srcdir)/complete-bundle.sh \
	$(srcdir)/create-dmg.sh \
	$(srcdir)/debug-bundle.sh \
	$(srcdir)/pgadmin.Info.plist \
	$(srcdir)/pgadmin.Info.plist.in \
	$(srcdir)/debug.pgadmin.Info.plist \
	$(srcdir)/debug.pgadmin.Info.plist.in \
	$(srcdir)/licence.r \
	$(srcdir)/pgAdmin3.icns \
	$(srcdir)/sql.icns \
	$(srcdir)/PkgInfo 

install-exec-hook:
if APPBUNDLE
	$(install_sh_DATA) PkgInfo $(bundledir)/Contents/PkgInfo
	$(install_sh_DATA) pgadmin.Info.plist $(bundledir)/Contents/Info.plist
	$(install_sh_DATA) "pgAdmin3.icns" "$(bundledir)/Contents/Resources/pgAdmin3.icns"
	$(install_sh_DATA) "sql.icns" "$(bundledir)/Contents/Resources/sql.icns"
	$$($(WX_CONFIG) --rescomp | sed 's/-t[[:space:]]*APPL//') \
		 "$(bundledir)/Contents/Resources/pgAdmin3.rsrc" -useDF
	$(install_sh_PROGRAM) "$$($(PG_CONFIG) --bindir)/pg_dump" "$(bundledir)/Contents/SharedSupport/pg_dump"
	$(install_sh_PROGRAM) "$$($(PG_CONFIG) --bindir)/pg_dumpall" "$(bundledir)/Contents/SharedSupport/pg_dumpall"
	$(install_sh_PROGRAM) "$$($(PG_CONFIG) --bindir)/pg_restore" "$(bundledir)/Contents/SharedSupport/pg_restore"
	$(install_sh_PROGRAM) "$$($(PG_CONFIG) --bindir)/psql" "$(bundledir)/Contents/SharedSupport/psql"
	./complete-bundle.sh "$(bundledir)"
endif
