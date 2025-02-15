# Automatically generated GNU Makefile. Qui Nov  3 15:38:45 BRST 2011
# fgen v0.3 (C) 1997,98 Beroud Jean-Marc

# Determine platform
UMACHINE := $(shell uname -m)

# simultaneous parallel jobs & load average limit
MAXJOBS = 1
MAXLOAD = 1

# standard
SHELL     = sh
MAKE      = make
MAKEFILE  = Makefile
MAKEFLAGS = -r -j$(MAXJOBS) -l$(MAXLOAD)

# utils
FGEN    = fgen
F2HTML  = f2html
ECHO    = echo
RM      = rm
CP      = cp
MV      = mv
CD      = cd
MKDIR   = mkdir
TAR     = tar
GZIP    = gzip
INSTALL = install

# dirs
libdir = ./

# preprocessor, compilers, linker & archiver
ifeq ($(SCAN_ARCH),Darwin_intel)
   FPP = gcc
   CC  = gcc
   FC  = ifort
   LD  = ifort
   AR  = ar
endif

ifeq ($(SCAN_ARCH),cray_pgi)
   FPP = cc
   CC  = cc
   FC  = ftn
   LD  = ftn
   AR  = ar
endif

ifeq ($(SCAN_ARCH),GNU_Linux)
   FPP = cc
   CC  = cc
   FC  = gfortran
   LD  = gfortran
   AR  = ar
endif
# default mode (max. optimization)
mode = opt

# header file directories
CCFLAGS = 
FFLAGS  = 

# default flags
FPPFLAGS = -C -E
CCFLAGS += 
FFLAGS  += 
LDFLAGS  = 
ARFLAGS  = -r

# add flags for debugging if requested
ifeq (dbg,$(findstring dbg,$(mode)))
   CCFLAGS += -g -Wall
   FFLAGS  += -g -Wall
   LDFLAGS += -g
endif

# add flags for profiling if requested
ifeq (pro,$(findstring pro,$(mode)))
   CCFLAGS += -pg
   FFLAGS  += 
   LDFLAGS += 
endif

# add flags for optimization if requested
ifeq (opt,$(findstring opt,$(mode)))
   CCFLAGS += -O2
   FFLAGS  += -O2
   LDFLAGS += 
endif

# objectlist file
include Makefile-objs

# additionnal libraries
LIBDIRS = -L$(libdir)  
LIBS    = -lmpeu  

# target names
BIN = 
LIB = libmpeu.a

# Not real file targets
.PHONY: $(MAKEFILE) Makefile-deps Makefile-objs \
        all dep html clean install help

# targets
all: $(LIB) $(BIN)

$(LIB): $(OBJS)
	@$(ECHO) ""
	@$(ECHO) "Creating archive $(@F)"
	@$(ECHO) ""
	$(AR) $(ARFLAGS) $@ $(notdir $(OBJS))


$(BIN): $(OBJS) 
	@$(ECHO) ""
	@$(ECHO) "Linking executable $(@F)"
	@$(ECHO) ""
	$(LD) $(LDFLAGS) $(notdir $(OBJS)) $(LIBDIRS) $(LIBS) -o $@

# args for fgen & f2html
FGENARGS   = -l $(libdir) 
F2HTMLARGS = $(libdir) 

# rebuild dependencies
dep:
	@$(FGEN) -d $(FGENARGS)

# build html pages
HTMLDIR = html

html:
	@$(F2HTML) -d $(HTMLDIR) $(F2HTMLARGS) 

# cleanup
clean:
	$(RM) -f $(BIN) $(LIB) $(notdir $(OBJS)) *.[dlMT] *.lst *.mod work.pc* core

# installation
LIBDIR = /usr/local/lib
BINDIR = /usr/local/bin

install:
	if [ -n "$(LIB)" ] && [ -r "$(LIB)" ]; then \
	   $(INSTALL) -m 644 $(LIB) $(LIBDIR); \
	fi
	if [ -n "$(BIN)" ] && [ -r "$(BIN)" ]; then \
	   $(INSTALL) -c $(BIN) $(BINDIR); \
	fi

# suffixes
.SUFFIXES:
.SUFFIXES: .h .F .f .F90 .f90 .c .o

# remove target on error
.DELETE_ON_ERROR:

# implicit rules
# Want full path? Change $(<F) to $< and add -o $(@F) or -o $@
%.o: %.F   ; $(FC) -c $(FFLAGS)  $(<F)
%.o: %.f   ; $(FC) -c $(FFLAGS)  $(<F)
%.o: %.F90 ; $(FC) -c $(FFLAGS)  $(<F)
%.o: %.f90 ; $(FC) -c $(FFLAGS)  $(<F)
%.o: %.c   ; $(CC) -c $(CCFLAGS) $(<F)

# if the compiler do no support the F90 extension
#%.o: %.F90
#	$(MV) $(<F) $(*F).c
#	$(FPP) $(FPPFLAGS) $(*F).c > $(*F)-tmp.f90
#	$(FC) -c $(FFLAGS) $(INCDIRS) $(*F)-tmp.f90
#	$(MV) $(*F)-tmp.o $(*F).o
#	$(RM) -f $(*F).c $(*F)-tmp.f90 

# help page
help:
	@$(ECHO) "Defined targets:"
	@$(ECHO) "  all    : build targets (default)"
	@$(ECHO) "  dep    : build dependencies"
	@$(ECHO) "  html   : build html pages"
	@$(ECHO) "  clean  : cleanup"
	@$(ECHO) "  install: install executable"
	@$(ECHO) "Defined modes:"
	@$(ECHO) "  opt: enable flags for optimization (default)"
	@$(ECHO) "  dbg: enable flags for debugging"
	@$(ECHO) "  pro: enable flags for profiling"
	@$(ECHO) "Example:"
	@$(ECHO) "  type \`make mode=dbg+pro' to enable dbg and pro flags"

# dependencies file
include Makefile-deps
