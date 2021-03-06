## Process this file with automake to create Makefile.in
## Makefile for libdw.
##
## Copyright (C) 2002, 2003, 2004 Red Hat, Inc.
##
## This program is Open Source software; you can redistribute it and/or
## modify it under the terms of the Open Software License version 1.0 as
## published by the Open Source Initiative.
##
## You should have received a copy of the Open Software License along
## with this program; if not, you may obtain a copy of the Open Software
## License version 1.0 from http://www.opensource.org/licenses/osl.php or
## by writing the Open Source Initiative c/o Lawrence Rosen, Esq.,
## 3001 King Ranch Road, Ukiah, CA 95482.
##
DEFS = -D_GNU_SOURCE -DHAVE_CONFIG_H
if MUDFLAP
AM_CFLAGS = -Wall -Wshadow -std=gnu99
else
AM_CFLAGS = -Wall -Werror -Wshadow -std=gnu99
endif
INCLUDES = -I. -I$(srcdir) -I$(srcdir)/../libelf -I.. -I$(srcdir)/../lib
VERSION = 1

lib_LIBRARIES = libdw.a
if !MUDFLAP
noinst_LIBRARIES = libdw_pic.a
noinst_PROGRAMS = $(noinst_LIBRARIES:_pic.a=.so)
endif

include_HEADERS = dwarf.h
euincludedir = ${includedir}/elfutils
euinclude_HEADERS = libdw.h

libdw_a_SOURCES = dwarf_begin.c dwarf_begin_elf.c dwarf_end.c dwarf_getelf.c \
		  dwarf_getpubnames.c dwarf_getabbrev.c dwarf_tag.c \
		  dwarf_error.c dwarf_nextcu.c dwarf_diename.c dwarf_offdie.c \
		  dwarf_attr.c dwarf_formstring.c dwarf_abbrev_hash.c \
		  dwarf_child.c dwarf_haschildren.c dwarf_formaddr.c \
		  dwarf_formudata.c dwarf_formsdata.c dwarf_lowpc.c \
		  dwarf_highpc.c dwarf_formref.c dwarf_siblingof.c \
		  dwarf_dieoffset.c dwarf_cuoffset.c dwarf_hasattr.c \
		  dwarf_hasform.c dwarf_whatform.c dwarf_whatattr.c \
		  dwarf_bytesize.c dwarf_arrayorder.c dwarf_bitsize.c \
		  dwarf_bitoffset.c dwarf_srclang.c dwarf_getabbrevtag.c \
		  dwarf_getabbrevcode.c dwarf_abbrevhaschildren.c \
		  dwarf_getattrcnt.c dwarf_getabbrevattr.c \
		  dwarf_getsrclines.c dwarf_getsrc_die.c \
		  dwarf_linesrc.c dwarf_lineno.c dwarf_lineaddr.c \
		  dwarf_linecol.c dwarf_linebeginstatement.c \
		  dwarf_lineendsequence.c dwarf_lineblock.c \
		  dwarf_lineprologueend.c dwarf_lineepiloguebegin.c \
		  dwarf_onesrcline.c dwarf_formblock.c \
		  dwarf_getsrcfiles.c dwarf_filesrc.c \
		  dwarf_getloclist.c dwarf_getstring.c dwarf_offabbrev.c \
		  dwarf_getaranges.c dwarf_onearange.c dwarf_getarangeinfo.c \
		  dwarf_getarange_addr.c dwarf_getattrs.c dwarf_formflag.c \
		  dwarf_getmacros.c \
		  libdw_findcu.c libdw_form.c libdw_alloc.c


if !MUDFLAP
libdw_pic_a_SOURCES =
am_libdw_pic_a_OBJECTS = $(libdw_a_SOURCES:.c=.os)

libdw_so_SOURCES =
libdw.so: libdw_pic.a $(srcdir)/libdw.map
	$(CC) -shared -o $@ -Wl,--whole-archive,$<,--no-whole-archive \
	      -Wl,--version-script,$(srcdir)/libdw.map,--no-undefined \
	      -Wl,--soname,$@.$(VERSION),-z,defs \
	      ../libelf/libelf.so
	ln -fs $@ $@.$(VERSION)


%.os: %.c %.o
	if $(COMPILE) -c -o $@ -fpic -DPIC -DSHARED -MT $@ -MD -MP \
	   -MF "$(DEPDIR)/$*.Tpo" `test -f '$<' || echo '$(srcdir)/'`$<; \
	then cat "$(DEPDIR)/$*.Tpo" >> "$(DEPDIR)/$*.Po"; \
	     rm -f "$(DEPDIR)/$*.Tpo"; \
	else rm -f "$(DEPDIR)/$*.Tpo"; exit 1; \
	fi

install: install-am libdw.so
	$(mkinstalldirs) $(DESTDIR)$(libdir)
	$(INSTALL_PROGRAM) libdw.so $(DESTDIR)$(libdir)/libdw-$(PACKAGE_VERSION).so
	ln -fs libdw-$(PACKAGE_VERSION).so $(DESTDIR)$(libdir)/libdw.so.$(VERSION)
	ln -fs libdw.so.$(VERSION) $(DESTDIR)$(libdir)/libdw.so

uninstall: uninstall-am
	rm -f $(DESTDIR)$(libdir)/libdw-$(PACKAGE_VERSION).so
	rm -f $(DESTDIR)$(libdir)/libdw.so.$(VERSION)
	rm -f $(DESTDIR)$(libdir)/libdw.so
	rmdir --ignore-fail-on-non-empty $(DESTDIR)$(includedir)/elfutils
endif

noinst_HEADERS = libdwP.h memory-access.h dwarf_abbrev_hash.h

EXTRA_DIST = libdw.map

CLEANFILES = $(am_libdw_pic_a_OBJECTS)
