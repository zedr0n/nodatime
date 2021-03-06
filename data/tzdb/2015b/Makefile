# This file is in the public domain, so clarified as of
# 2009-05-17 by Arthur David Olson.

# Package name for the code distribution.
PACKAGE=	tzcode

# Version numbers of the code and data distributions.
VERSION=	2015b

# Email address for bug reports.
BUGEMAIL=	tz@iana.org

# Change the line below for your time zone (after finding the zone you want in
# the time zone files, or adding it to a time zone file).
# Alternately, if you discover you've got the wrong time zone, you can just
#	zic -l rightzone
# to correct things.
# Use the command
#	make zonenames
# to get a list of the values you can use for LOCALTIME.

LOCALTIME=	GMT

# If you want something other than Eastern United States time as a template
# for handling POSIX-style time zone environment variables,
# change the line below (after finding the zone you want in the
# time zone files, or adding it to a time zone file).
# (When a POSIX-style environment variable is handled, the rules in the
# template file are used to determine "spring forward" and "fall back" days and
# times; the environment variable itself specifies UT offsets of standard and
# summer time.)
# Alternately, if you discover you've got the wrong time zone, you can just
#	zic -p rightzone
# to correct things.
# Use the command
#	make zonenames
# to get a list of the values you can use for POSIXRULES.
# If you want POSIX compatibility, use "America/New_York".

POSIXRULES=	America/New_York

# Also see TZDEFRULESTRING below, which takes effect only
# if the time zone files cannot be accessed.

# Everything gets put in subdirectories of. . .

TOPDIR=		/usr/local

# "Compiled" time zone information is placed in the "TZDIR" directory
# (and subdirectories).
# Use an absolute path name for TZDIR unless you're just testing the software.

TZDIR_BASENAME=	zoneinfo
TZDIR=		$(TOPDIR)/etc/$(TZDIR_BASENAME)

# Types to try, as an alternative to time_t.  int64_t should be first.
TIME_T_ALTERNATIVES= int64_t int32_t uint32_t uint64_t

# The "tzselect", "zic", and "zdump" commands get installed in. . .

ETCDIR=		$(TOPDIR)/etc

# If you "make INSTALL", the "date" command gets installed in. . .

BINDIR=		$(TOPDIR)/bin

# Manual pages go in subdirectories of. . .

MANDIR=		$(TOPDIR)/man

# Library functions are put in an archive in LIBDIR.

LIBDIR=		$(TOPDIR)/lib

# If you always want time values interpreted as "seconds since the epoch
# (not counting leap seconds)", use
#	REDO=		posix_only
# below.  If you always want right time values interpreted as "seconds since
# the epoch" (counting leap seconds)", use
#	REDO=		right_only
# below.  If you want both sets of data available, with leap seconds not
# counted normally, use
#	REDO=		posix_right
# below.  If you want both sets of data available, with leap seconds counted
# normally, use
#	REDO=		right_posix
# below.  If you want just POSIX-compatible time values, but with
# out-of-scope and often-wrong data from the file 'backzone', use
#	REDO=		posix_packrat
# POSIX mandates that leap seconds not be counted; for compatibility with it,
# use "posix_only", "posix_right", or "posix_packrat".

REDO=		posix_right

# Since "." may not be in PATH...

YEARISTYPE=	./yearistype

# Non-default libraries needed to link.
# Add -lintl if you want to use 'gettext' on Solaris.
LDLIBS=

# Add the following to the end of the "CFLAGS=" line as needed.
#  -DBIG_BANG=-9999999LL if the Big Bang occurred at time -9999999 (see zic.c)
#  -DHAVE_ADJTIME=0 if 'adjtime' does not exist (SVR0?)
#  -DHAVE_DOS_FILE_NAMES if file names have drive specifiers etc. (MS-DOS)
#  -DHAVE_GETTEXT=1 if 'gettext' works (GNU, Linux, Solaris); also see LDLIBS
#  -DHAVE_INCOMPATIBLE_CTIME_R=1 if your system's time.h declares
#	ctime_r and asctime_r incompatibly with the POSIX standard (Solaris 8).
#  -DHAVE_INTTYPES_H=1 if you have a pre-C99 compiler with "inttypes.h"
#  -DHAVE_LINK=0 if your system lacks a link function
#  -DHAVE_LOCALTIME_R=0 if your system lacks a localtime_r function
#  -DHAVE_LOCALTIME_RZ=0 if you do not want zdump to use localtime_rz
#	This defaults to 1 if a working localtime_rz seems to be available.
#	localtime_rz can make zdump significantly faster, but is nonstandard.
#  -DHAVE_SETTIMEOFDAY=0 if settimeofday does not exist (SVR0?)
#  -DHAVE_SETTIMEOFDAY=1 if settimeofday has just 1 arg (SVR4)
#  -DHAVE_SETTIMEOFDAY=2 if settimeofday uses 2nd arg (4.3BSD)
#  -DHAVE_SETTIMEOFDAY=3 if settimeofday ignores 2nd arg (4.4BSD)
#  -DHAVE_STDINT_H=1 if you have a pre-C99 compiler with "stdint.h"
#  -DHAVE_STRFTIME_L=1 if <time.h> declares locale_t and strftime_l
#	This defaults to 0 if _POSIX_VERSION < 200809, 1 otherwise.
#  -DHAVE_SYMLINK=0 if your system lacks the symlink function
#  -DHAVE_SYS_STAT_H=0 if your compiler lacks a "sys/stat.h"
#  -DHAVE_SYS_WAIT_H=0 if your compiler lacks a "sys/wait.h"
#  -DHAVE_TZSET=0 if your system lacks a tzset function
#  -DHAVE_UNISTD_H=0 if your compiler lacks a "unistd.h" (Microsoft C++ 7?)
#  -DHAVE_UTMPX_H=1 if your compiler has a "utmpx.h"
#  -DNO_RUN_TIME_WARNINGS_ABOUT_YEAR_2000_PROBLEMS_THANK_YOU=1
#	if you do not want run time warnings about formats that may cause
#	year 2000 grief
#  -Dssize_t=long on ancient hosts that lack ssize_t
#  -DTHREAD_SAFE=1 to make localtime.c thread-safe, as POSIX requires;
#	not needed by the main-program tz code, which is single-threaded.
#	Append other compiler flags as needed, e.g., -pthread on GNU/Linux.
#  -Dtime_tz=\"T\" to use T as the time_t type, rather than the system time_t
#  -DTZ_DOMAIN=\"foo\" to use "foo" for gettext domain name; default is "tz"
#  -DTZ_DOMAINDIR=\"/path\" to use "/path" for gettext directory;
#	the default is system-supplied, typically "/usr/lib/locale"
#  -DTZDEFRULESTRING=\",date/time,date/time\" to default to the specified
#	DST transitions if the time zone files cannot be accessed
#  -DUNINIT_TRAP=1 if reading uninitialized storage can cause problems
#	other than simply getting garbage data
#  -DUSE_LTZ=0 to build zdump with the system time zone library
#	Also set TZDOBJS=zdump.o and CHECK_TIME_T_ALTERNATIVES= below.
#  -DZIC_MAX_ABBR_LEN_WO_WARN=3
#	(or some other number) to set the maximum time zone abbreviation length
#	that zic will accept without a warning (the default is 6)
#  $(GCC_DEBUG_FLAGS) if you are using GCC and want lots of checking
GCC_DEBUG_FLAGS = -Dlint -g3 -O3 -fno-common -fstrict-aliasing \
	-Wall -Wextra \
	-Wbad-function-cast -Wcast-align -Wcast-qual \
	-Wdeclaration-after-statement \
	-Wformat=2 -Winit-self -Wjump-misses-init \
	-Wmissing-declarations -Wmissing-noreturn -Wmissing-prototypes \
	-Wnested-externs -Wno-address -Wno-cast-qual \
	-Wno-format-nonliteral -Wno-sign-compare -Wno-sign-conversion \
	-Wno-type-limits \
	-Wno-unused-parameter -Woverlength-strings -Wpointer-arith \
	-Wshadow -Wstrict-prototypes -Wsuggest-attribute=const \
	-Wsuggest-attribute=format -Wsuggest-attribute=noreturn \
	-Wsuggest-attribute=pure -Wtrampolines \
	-Wwrite-strings
#
# If you want to use System V compatibility code, add
#	-DUSG_COMPAT
# to the end of the "CFLAGS=" line.  This arrange for "timezone" and "daylight"
# variables to be kept up-to-date by the time conversion functions.  Neither
# "timezone" nor "daylight" is described in X3J11's work.
#
# If your system has a "GMT offset" field in its "struct tm"s
# (or if you decide to add such a field in your system's "time.h" file),
# add the name to a define such as
#	-DTM_GMTOFF=tm_gmtoff
# to the end of the "CFLAGS=" line.  If not defined, the code attempts to
# guess TM_GMTOFF from other macros; define NO_TM_GMTOFF to suppress this.
# Similarly, if your system has a "zone abbreviation" field, define
#	-DTM_ZONE=tm_zone
# and define NO_TM_ZONE to suppress any guessing.  These two fields are not
# required by POSIX, but are widely available on GNU/Linux and BSD systems.
#
# If you want functions that were inspired by early versions of X3J11's work,
# add
#	-DSTD_INSPIRED
# to the end of the "CFLAGS=" line.  This arranges for the functions
# "tzsetwall", "offtime", "timelocal", "timegm", "timeoff",
# "posix2time", and "time2posix" to be added to the time conversion library.
# "tzsetwall" is like "tzset" except that it arranges for local wall clock
# time (rather than the time specified in the TZ environment variable)
# to be used.
# "offtime" is like "gmtime" except that it accepts a second (long) argument
# that gives an offset to add to the time_t when converting it.
# "timelocal" is equivalent to "mktime".
# "timegm" is like "timelocal" except that it turns a struct tm into
# a time_t using UT (rather than local time as "timelocal" does).
# "timeoff" is like "timegm" except that it accepts a second (long) argument
# that gives an offset to use when converting to a time_t.
# "posix2time" and "time2posix" are described in an included manual page.
# X3J11's work does not describe any of these functions.
# Sun has provided "tzsetwall", "timelocal", and "timegm" in SunOS 4.0.
# These functions may well disappear in future releases of the time
# conversion package.
#
# If you don't want functions that were inspired by NetBSD, add
#	-DNETBSD_INSPIRED=0
# to the end of the "CFLAGS=" line.  Otherwise, the functions
# "localtime_rz", "mktime_z", "tzalloc", and "tzfree" are added to the
# time library, and if STD_INSPIRED is also defined the functions
# "posix2time_z" and "time2posix_z" are added as well.
# The functions ending in "_z" (or "_rz") are like their unsuffixed
# (or suffixed-by-"_r") counterparts, except with an extra first
# argument of opaque type timezone_t that specifies the time zone.
# "tzalloc" allocates a timezone_t value, and "tzfree" frees it.
#
# If you want to allocate state structures in localtime, add
#	-DALL_STATE
# to the end of the "CFLAGS=" line.  Storage is obtained by calling malloc.
#
# If you want an "altzone" variable (a la System V Release 3.1), add
#	-DALTZONE
# to the end of the "CFLAGS=" line.
# This variable is not described in X3J11's work.
#
# NIST-PCTS:151-2, Version 1.4, (1993-12-03) is a test suite put
# out by the National Institute of Standards and Technology
# which claims to test C and Posix conformance.  If you want to pass PCTS, add
#	-DPCTS
# to the end of the "CFLAGS=" line.
#
# If you want strict compliance with XPG4 as of 1994-04-09, add
#	-DXPG4_1994_04_09
# to the end of the "CFLAGS=" line.  This causes "strftime" to always return
# 53 as a week number (rather than 52 or 53) for those days in January that
# before the first Monday in January when a "%V" format is used and January 1
# falls on a Friday, Saturday, or Sunday.

CFLAGS=

# Linker flags.  Default to $(LFLAGS) for backwards compatibility
# to tzcode2012h and earlier.

LDFLAGS=	$(LFLAGS)

zic=		./zic
ZIC=		$(zic) $(ZFLAGS)

ZFLAGS=

# The name of a Posix-compliant 'awk' on your system.
AWK=		awk

# The full path name of a Posix-compliant shell, preferably one that supports
# the Korn shell's 'select' statement as an extension.
# These days, Bash is the most popular.
# It should be OK to set this to /bin/sh, on platforms where /bin/sh
# lacks 'select' or doesn't completely conform to Posix, but /bin/bash
# is typically nicer if it works.
KSHELL=		/bin/bash

# The path where SGML DTDs are kept and the catalog file(s) to use when
# validating.  The default is appropriate for Ubuntu 13.10.
SGML_TOPDIR= /usr
SGML_DTDDIR= $(SGML_TOPDIR)/share/xml/w3c-sgml-lib/schema/dtd
SGML_SEARCH_PATH= $(SGML_DTDDIR)/REC-html401-19991224
SGML_CATALOG_FILES= \
  $(SGML_TOPDIR)/share/doc/w3-recs/html/www.w3.org/TR/1999/REC-html401-19991224/HTML4.cat

# The name, arguments and environment of a program to validate your web pages.
# See <http://www.jclark.com/sp/> for a validator, and
# <http://validator.w3.org/source/> for a validation library.
VALIDATE = nsgmls
VALIDATE_FLAGS = -s -B -wall -wno-unused-param
VALIDATE_ENV = \
  SGML_CATALOG_FILES=$(SGML_CATALOG_FILES) \
  SGML_SEARCH_PATH=$(SGML_SEARCH_PATH) \
  SP_CHARSET_FIXED=YES \
  SP_ENCODING=UTF-8

# This expensive test requires USE_LTZ.
# To suppress it, define this macro to be empty.
CHECK_TIME_T_ALTERNATIVES = check_time_t_alternatives

# SAFE_CHAR is a regular expression that matches a safe character.
# Some parts of this distribution are limited to safe characters;
# others can use any UTF-8 character.
# For now, the safe characters are a safe subset of ASCII.
# The caller must set the shell variable 'sharp' to the character '#',
# since Makefile macros cannot contain '#'.
# TAB_CHAR is a single tab character, in single quotes.
TAB_CHAR=	'	'
SAFE_CHARSET1=	$(TAB_CHAR)' !\"'$$sharp'$$%&'\''()*+,./0123456789:;<=>?@'
SAFE_CHARSET2=	'ABCDEFGHIJKLMNOPQRSTUVWXYZ[\\^_`'
SAFE_CHARSET3=	'abcdefghijklmnopqrstuvwxyz{|}~'
SAFE_CHARSET=	]$(SAFE_CHARSET1)$(SAFE_CHARSET2)$(SAFE_CHARSET3)-
SAFE_CHAR=	'['$(SAFE_CHARSET)']'
# NONSYM_CHAR is a regular expression that matches any character
# except for a small number of symbols, where we prefer to stick with
# ASCII renderings for the convenience of maintainers whose text editors
# mishandle UTF-8 by default (e.g., XEmacs 21.4.22).
NONSYM_CHAR=	'[^–—°′″≈≠≤≥±−×÷∞←→↔·•§¶«»‘’‚‛“”„‟‹›「」『』〝〞〟]'

# SAFE_LINE matches a line of safe characters.
# SAFE_SHARP_LINE is similar, except any character can follow '#';
# this is so that comments can contain non-ASCII characters.
# NONSYM_LINE matches a line of non-symbols.
# VALID_LINE matches a line of any validly-encoded characters.
SAFE_LINE=	'^'$(SAFE_CHAR)'*$$'
SAFE_SHARP_LINE='^'$(SAFE_CHAR)'*('$$sharp$(NONSYM_CHAR)'*)?$$'
NONSYM_LINE=	'^'$(NONSYM_CHAR)'*$$'
VALID_LINE=	'^.*$$'

# Flags to give 'tar' when making a distribution.
# Try to use flags appropriate for GNU tar.
GNUTARFLAGS=	--numeric-owner --owner=0 --group=0 --mode=go+u,go-w
TARFLAGS=	`if tar $(GNUTARFLAGS) --version >/dev/null 2>&1; \
		 then echo $(GNUTARFLAGS); \
		 else :; \
		 fi`

# Flags to give 'gzip' when making a distribution.
GZIPFLAGS=	-9n

###############################################################################

cc=		cc
CC=		$(cc) -DTZDIR=\"$(TZDIR)\"

AR=		ar

# ':' on typical hosts; 'ranlib' on the ancient hosts that still need ranlib.
RANLIB=		:

TZCOBJS=	zic.o scheck.o ialloc.o
TZDOBJS=	zdump.o localtime.o asctime.o
DATEOBJS=	date.o localtime.o strftime.o asctime.o
LIBSRCS=	localtime.c asctime.c difftime.c
LIBOBJS=	localtime.o asctime.o difftime.o
HEADERS=	tzfile.h private.h
NONLIBSRCS=	zic.c zdump.c scheck.c ialloc.c
NEWUCBSRCS=	date.c strftime.c
SOURCES=	$(HEADERS) $(LIBSRCS) $(NONLIBSRCS) $(NEWUCBSRCS) \
			tzselect.ksh workman.sh
MANS=		newctime.3 newstrftime.3 newtzset.3 time2posix.3 \
			tzfile.5 tzselect.8 zic.8 zdump.8
MANTXTS=	newctime.3.txt newstrftime.3.txt newtzset.3.txt \
			time2posix.3.txt \
			tzfile.5.txt tzselect.8.txt zic.8.txt zdump.8.txt \
			date.1.txt
COMMON=		CONTRIBUTING Makefile NEWS README Theory
WEB_PAGES=	tz-art.htm tz-link.htm
DOCS=		$(MANS) date.1 $(MANTXTS) $(WEB_PAGES)
PRIMARY_YDATA=	africa antarctica asia australasia \
		europe northamerica southamerica
YDATA=		$(PRIMARY_YDATA) pacificnew etcetera backward
NDATA=		systemv factory
TDATA=		$(YDATA) $(NDATA)
ZONETABLES=	zone1970.tab zone.tab
TABDATA=	iso3166.tab leapseconds $(ZONETABLES)
LEAP_DEPS=	leapseconds.awk leap-seconds.list
DATA=		$(YDATA) $(NDATA) backzone $(TABDATA) \
			leap-seconds.list yearistype.sh
AWK_SCRIPTS=	checklinks.awk checktab.awk leapseconds.awk
MISC=		$(AWK_SCRIPTS) zoneinfo2tdf.pl
ENCHILADA=	$(COMMON) $(DOCS) $(SOURCES) $(DATA) $(MISC)

# And for the benefit of csh users on systems that assume the user
# shell should be used to handle commands in Makefiles. . .

SHELL=		/bin/sh

all:		tzselect zic zdump libtz.a $(TABDATA)

ALL:		all date

install:	all $(DATA) $(REDO) $(MANS)
		mkdir -p $(DESTDIR)$(ETCDIR) $(DESTDIR)$(TZDIR) \
			$(DESTDIR)$(LIBDIR) \
			$(DESTDIR)$(MANDIR)/man3 $(DESTDIR)$(MANDIR)/man5 \
			$(DESTDIR)$(MANDIR)/man8
		$(ZIC) -y $(YEARISTYPE) \
			-d $(DESTDIR)$(TZDIR) -l $(LOCALTIME) -p $(POSIXRULES)
		cp -f iso3166.tab $(ZONETABLES) $(DESTDIR)$(TZDIR)/.
		cp tzselect zic zdump $(DESTDIR)$(ETCDIR)/.
		cp libtz.a $(DESTDIR)$(LIBDIR)/.
		$(RANLIB) $(DESTDIR)$(LIBDIR)/libtz.a
		cp -f newctime.3 newtzset.3 $(DESTDIR)$(MANDIR)/man3/.
		cp -f tzfile.5 $(DESTDIR)$(MANDIR)/man5/.
		cp -f tzselect.8 zdump.8 zic.8 $(DESTDIR)$(MANDIR)/man8/.

INSTALL:	ALL install date.1
		mkdir -p $(DESTDIR)$(BINDIR) $(DESTDIR)$(MANDIR)/man1
		cp date $(DESTDIR)$(BINDIR)/.
		cp -f date.1 $(DESTDIR)$(MANDIR)/man1/.

version.h:
		(echo 'static char const PKGVERSION[]="($(PACKAGE)) ";' && \
		 echo 'static char const TZVERSION[]="$(VERSION)";' && \
		 echo 'static char const REPORT_BUGS_TO[]="$(BUGEMAIL)";') >$@

zdump:		$(TZDOBJS)
		$(CC) -o $@ $(CFLAGS) $(LDFLAGS) $(TZDOBJS) $(LDLIBS)

zic:		$(TZCOBJS) yearistype
		$(CC) -o $@ $(CFLAGS) $(LDFLAGS) $(TZCOBJS) $(LDLIBS)

yearistype:	yearistype.sh
		cp yearistype.sh yearistype
		chmod +x yearistype

leapseconds:	$(LEAP_DEPS)
		$(AWK) -f leapseconds.awk leap-seconds.list >$@

posix_only:	zic $(TDATA)
		$(ZIC) -y $(YEARISTYPE) -d $(DESTDIR)$(TZDIR) \
			-L /dev/null $(TDATA)

right_only:	zic leapseconds $(TDATA)
		$(ZIC) -y $(YEARISTYPE) -d $(DESTDIR)$(TZDIR) \
			-L leapseconds $(TDATA)

# In earlier versions of this makefile, the other two directories were
# subdirectories of $(TZDIR).  However, this led to configuration errors.
# For example, with posix_right under the earlier scheme,
# TZ='right/Australia/Adelaide' got you localtime with leap seconds,
# but gmtime without leap seconds, which led to problems with applications
# like sendmail that subtract gmtime from localtime.
# Therefore, the other two directories are now siblings of $(TZDIR).
# You must replace all of $(TZDIR) to switch from not using leap seconds
# to using them, or vice versa.
right_posix:	right_only leapseconds
		rm -fr $(DESTDIR)$(TZDIR)-leaps
		ln -s $(TZDIR_BASENAME) $(DESTDIR)$(TZDIR)-leaps || \
		  $(ZIC) -y $(YEARISTYPE) -d $(DESTDIR)$(TZDIR)-leaps \
			-L leapseconds $(TDATA)
		$(ZIC) -y $(YEARISTYPE) -d $(DESTDIR)$(TZDIR)-posix \
			-L /dev/null $(TDATA)

posix_right:	posix_only leapseconds
		rm -fr $(DESTDIR)$(TZDIR)-posix
		ln -s $(TZDIR_BASENAME) $(DESTDIR)$(TZDIR)-posix || \
		  $(ZIC) -y $(YEARISTYPE) -d $(DESTDIR)$(TZDIR)-posix \
			-L /dev/null $(TDATA)
		$(ZIC) -y $(YEARISTYPE) -d $(DESTDIR)$(TZDIR)-leaps \
			-L leapseconds $(TDATA)

posix_packrat:	posix_only backzone
		$(AWK) '/^Rule/' $(TDATA) | \
		  $(ZIC) -y $(YEARISTYPE) -d $(DESTDIR)$(TZDIR) \
			-L /dev/null - backzone

zones:		$(REDO)

libtz.a:	$(LIBOBJS)
		$(AR) ru $@ $(LIBOBJS)
		$(RANLIB) $@

date:		$(DATEOBJS)
		$(CC) -o $@ $(CFLAGS) $(LDFLAGS) $(DATEOBJS) $(LDLIBS)

tzselect:	tzselect.ksh
		sed \
			-e 's|#!/bin/bash|#!$(KSHELL)|g' \
			-e 's|AWK=[^}]*|AWK=$(AWK)|g' \
			-e 's|\(PKGVERSION\)=.*|\1='\''($(PACKAGE)) '\''|' \
			-e 's|\(REPORT_BUGS_TO\)=.*|\1=$(BUGEMAIL)|' \
			-e 's|TZDIR=[^}]*|TZDIR=$(TZDIR)|' \
			-e 's|\(TZVERSION\)=.*|\1=$(VERSION)|' \
			<$? >$@
		chmod +x $@

check:		check_character_set check_white_space check_links check_sorted \
		  check_tables check_web

check_character_set: $(ENCHILADA)
		LC_ALL=en_US.utf8 && export LC_ALL && \
		sharp='#' && \
		! grep -Env $(SAFE_LINE) $(MANS) date.1 $(MANTXTS) \
			$(MISC) $(SOURCES) $(WEB_PAGES) && \
		! grep -Env $(SAFE_SHARP_LINE) $(TDATA) backzone \
			iso3166.tab leapseconds yearistype.sh zone.tab && \
		test $$(grep -Ecv $(SAFE_SHARP_LINE) Makefile) -eq 1 && \
		! grep -Env $(NONSYM_LINE) CONTRIBUTING NEWS README Theory \
			$(MANS) date.1 zone1970.tab && \
		! grep -Env $(VALID_LINE) $(ENCHILADA)

check_white_space: $(ENCHILADA)
		! grep -En ' '$(TAB_CHAR)"|$$(printf '[\f\r\v]')" $(ENCHILADA)
		! grep -n '[[:space:]]$$' $(ENCHILADA)

CHECK_CC_LIST = { n = split($$1,a,/,/); for (i=2; i<=n; i++) print a[1], a[i]; }

check_sorted: backward backzone iso3166.tab zone.tab zone1970.tab
		$(AWK) '/^Link/ {print $$3}' backward | LC_ALL=C sort -cu
		$(AWK) '/^Zone/ {print $$2}' backzone | LC_ALL=C sort -cu
		$(AWK) '/^[^#]/ {print $$1}' iso3166.tab | LC_ALL=C sort -cu
		$(AWK) '/^[^#]/ {print $$1}' zone.tab | LC_ALL=C sort -c
		$(AWK) '/^[^#]/ {print substr($$0, 1, 2)}' zone1970.tab | \
		  LC_ALL=C sort -c
		$(AWK) '/^[^#]/ $(CHECK_CC_LIST)' zone1970.tab | \
		  LC_ALL=C sort -cu

check_links:	checklinks.awk $(TDATA)
		$(AWK) -f checklinks.awk $(TDATA)

check_tables:	checktab.awk $(PRIMARY_YDATA) $(ZONETABLES)
		for tab in $(ZONETABLES); do \
		  $(AWK) -f checktab.awk -v zone_table=$$tab $(PRIMARY_YDATA) \
		    || exit; \
		done

check_web:	$(WEB_PAGES)
		$(VALIDATE_ENV) $(VALIDATE) $(VALIDATE_FLAGS) $(WEB_PAGES)

clean_misc:
		rm -f core *.o *.out \
		  date tzselect version.h zdump zic yearistype libtz.a
clean:		clean_misc
		rm -fr tzpublic

maintainer-clean: clean
		@echo 'This command is intended for maintainers to use; it'
		@echo 'deletes files that may need special tools to rebuild.'
		rm -f leapseconds $(MANTXTS) *.asc *.tar.gz

names:
		@echo $(ENCHILADA)

public:		check check_public $(CHECK_TIME_T_ALTERNATIVES) \
		tarballs signatures

date.1.txt:	date.1
newctime.3.txt:	newctime.3
newstrftime.3.txt: newstrftime.3
newtzset.3.txt:	newtzset.3
time2posix.3.txt: time2posix.3
tzfile.5.txt:	tzfile.5
tzselect.8.txt:	tzselect.8
zdump.8.txt:	zdump.8
zic.8.txt:	zic.8

$(MANTXTS):	workman.sh
		LC_ALL=C sh workman.sh `expr $@ : '\(.*\)\.txt$$'` >$@

# Set the time stamps to those of the git repository, if available,
# and if the files have not changed since then.
# This uses GNU 'touch' syntax 'touch -d@N FILE',
# where N is the number of seconds since 1970.
# If git or GNU 'touch' is absent, don't bother to sync with git timestamps.
# Also, set the timestamp of each prebuilt file like 'leapseconds'
# to be the maximum of the files it depends on.
set-timestamps.out: $(ENCHILADA)
		rm -f $@
		if files=`git ls-files $(ENCHILADA)` && \
		   touch -md @1 test.out; then \
		  rm -f test.out && \
		  for file in $$files; do \
		    if git diff --quiet $$file; then \
		      time=`git log -1 --format='tformat:%ct' $$file` && \
		      touch -cmd @$$time $$file; \
		    else \
		      echo >&2 "$$file: warning: does not match repository"; \
		    fi || exit; \
		  done; \
		fi
		touch -cmr `ls -t $(LEAP_DEPS) | sed 1q` leapseconds
		for file in `ls $(MANTXTS) | sed 's/\.txt$$//'`; do \
		  touch -cmr `ls -t $$file workman.sh | sed 1q` $$file.txt || \
		    exit; \
		done
		touch $@

# The zics below ensure that each data file can stand on its own.
# We also do an all-files run to catch links to links.

check_public:	$(ENCHILADA)
		make maintainer-clean
		make "CFLAGS=$(GCC_DEBUG_FLAGS)" $(ENCHILADA) all
		mkdir tzpublic
		for i in $(TDATA) ; do \
		  $(zic) -v -d tzpublic $$i 2>&1 || exit; \
		done
		$(zic) -v -d tzpublic $(TDATA)
		rm -fr tzpublic

# Check that the code works under various alternative
# implementations of time_t.
check_time_t_alternatives:
		if diff -q Makefile Makefile 2>/dev/null; then \
		  quiet_option='-q'; \
		else \
		  quiet_option=''; \
		fi && \
		zones=`$(AWK) '/^[^#]/ { print $$3 }' <zone1970.tab` && \
		for type in $(TIME_T_ALTERNATIVES); do \
		  mkdir -p tzpublic/$$type && \
		  make clean_misc && \
		  make TOPDIR=`pwd`/tzpublic/$$type \
		    CFLAGS='$(CFLAGS) -Dtime_tz='"'$$type'" \
		    REDO='$(REDO)' \
		    install && \
		  diff $$quiet_option -r \
		    tzpublic/int64_t/etc/zoneinfo \
		    tzpublic/$$type/etc/zoneinfo && \
		  case $$type in \
		  int32_t) range=-2147483648,2147483647;; \
		  uint32_t) range=0,4294967296;; \
		  int64_t) continue;; \
		  *u*) range=0,10000000000;; \
		  *) range=-10000000000,10000000000;; \
		  esac && \
		  echo checking $$type zones ... && \
		  tzpublic/int64_t/etc/zdump -V -t $$range $$zones \
		      >tzpublic/int64_t.out && \
		  tzpublic/$$type/etc/zdump -V -t $$range $$zones \
		      >tzpublic/$$type.out && \
		  diff -u tzpublic/int64_t.out tzpublic/$$type.out \
		    || exit; \
		done
		rm -fr tzpublic

tarballs:	tzcode$(VERSION).tar.gz tzdata$(VERSION).tar.gz

tzcode$(VERSION).tar.gz: set-timestamps.out
		LC_ALL=C && export LC_ALL && \
		tar $(TARFLAGS) -cf - \
		    $(COMMON) $(DOCS) $(SOURCES) | \
		  gzip $(GZIPFLAGS) > $@

tzdata$(VERSION).tar.gz: set-timestamps.out
		LC_ALL=C && export LC_ALL && \
		tar $(TARFLAGS) -cf - $(COMMON) $(DATA) $(MISC) | \
		  gzip $(GZIPFLAGS) > $@

signatures:	tzcode$(VERSION).tar.gz.asc tzdata$(VERSION).tar.gz.asc

tzcode$(VERSION).tar.gz.asc: tzcode$(VERSION).tar.gz
		gpg --armor --detach-sign $?

tzdata$(VERSION).tar.gz.asc: tzdata$(VERSION).tar.gz
		gpg --armor --detach-sign $?

typecheck:
		make clean
		for i in "long long" unsigned; \
		do \
			make CFLAGS="-DTYPECHECK -D__time_t_defined -D_TIME_T \"-Dtime_t=$$i\"" ; \
			./zdump -v Europe/Rome ; \
			make clean ; \
		done

zonenames:	$(TDATA)
		@$(AWK) '/^Zone/ { print $$2 } /^Link/ { print $$3 }' $(TDATA)

asctime.o:	private.h tzfile.h
date.o:		private.h
difftime.o:	private.h
ialloc.o:	private.h
localtime.o:	private.h tzfile.h
scheck.o:	private.h
strftime.o:	private.h tzfile.h
zdump.o:	version.h
zic.o:		private.h tzfile.h version.h

.KEEP_STATE:

.PHONY: ALL INSTALL all
.PHONY: check check_character_set check_links
.PHONY: check_public check_sorted check_tables
.PHONY: check_time_t_alternatives check_web check_white_space clean clean_misc
.PHONY: install maintainer-clean names posix_packrat posix_only posix_right
.PHONY: public right_only right_posix signatures tarballs typecheck
.PHONY: zonenames zones
