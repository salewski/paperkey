ACLOCAL_AMFLAGS=-I gl/m4
EXTRA_DIST=paperkey.spec $(man_MANS)
SUBDIRS=gl .

AM_CPPFLAGS=-I$(top_srcdir)/gl
LDADD=gl/libgl.a

man_MANS=paperkey.1

bin_PROGRAMS=paperkey

paperkey_SOURCES=paperkey.c packets.c packets.h parse.c parse.h extract.c extract.h restore.c restore.h output.c output.h

if USING_GCC
AM_CPPFLAGS+=-Wall -W -pedantic
endif

# Only do the self test if we're not cross compiling
if !CROSS_COMPILING
SUBDIRS+=checks
endif

if MINGW32_BUILD
CLEANFILES=paperkey.txt
EXTRA_DIST+=README.WIN32 paperkey.txt paperkey.exe
paperkey.txt: paperkey.1
	nroff -u0 -man paperkey.1 | col -b > paperkey.txt
endif
