#**************************************************************************
#*                                                                        *
#*                                 OCaml                                  *
#*                                                                        *
#*            Xavier Leroy, projet Cristal, INRIA Rocquencourt            *
#*                                                                        *
#*   Copyright 1999 Institut National de Recherche en Informatique et     *
#*     en Automatique.                                                    *
#*                                                                        *
#*   All rights reserved.  This file is distributed under the terms of    *
#*   the GNU Lesser General Public License version 2.1, with the          *
#*   special exception on linking described in the file LICENSE.          *
#*                                                                        *
#**************************************************************************

LIBNAME=bigarray
EXTRACFLAGS=-I../$(UNIXLIB) -DIN_OCAML_BIGARRAY
EXTRACAMLFLAGS=-I ../$(UNIXLIB)
COBJS=mmap_ba.$(O) mmap.$(O)
CAMLOBJS=bigarray.cmo

include ../Makefile.otherlibs.common

ifeq "$(SYSTEM)" "mingw"
LDOPTS=-ldopt "-link -static-libgcc"
endif

mmap.$(O): ../$(UNIXLIB)/mmap.c
	$(CC) -c $(OC_CFLAGS) $(OC_CPPFLAGS) $(OUTPUTOBJ)$@ $<
mmap_ba.$(O): ../unix/mmap_ba.c
	$(CC) -c $(OC_CFLAGS) $(OC_CPPFLAGS) $(OUTPUTOBJ)$@ $<

.PHONY: depend

depend:
	$(CAMLRUN) $(ROOTDIR)/tools/ocamldep -slash *.mli *.ml > .depend

include .depend
