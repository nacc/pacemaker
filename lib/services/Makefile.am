# Copyright (c) 2012 David Vossel <davidvossel@gmail.com>
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
# 
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Lesser General Public License for more details.
# 
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the Free Software
# Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA
#
#

MAINTAINERCLEANFILES = Makefile.in

AM_CPPFLAGS			= -I$(top_builddir)/include

lib_LTLIBRARIES			= libcrmservice.la
noinst_HEADERS			= pcmk-dbus.h upstart.h systemd.h services_private.h

libcrmservice_la_LDFLAGS	= -version-info 4:1:1
libcrmservice_la_CPPFLAGS	= -DOCF_ROOT_DIR=\"@OCF_ROOT_DIR@\" $(AM_CPPFLAGS)
libcrmservice_la_CFLAGS		= $(GIO_CFLAGS)

libcrmservice_la_CFLAGS		+= $(CFLAGS_HARDENED_LIB)
libcrmservice_la_LDFLAGS	+= $(LDFLAGS_HARDENED_LIB)

libcrmservice_la_LIBADD		= $(GIO_LIBS) $(top_builddir)/lib/common/libcrmcommon.la $(DBUS_LIBS)

libcrmservice_la_SOURCES	= services.c services_linux.c
if BUILD_DBUS
libcrmservice_la_SOURCES	+= dbus.c
endif
if BUILD_UPSTART
libcrmservice_la_SOURCES	+= upstart.c
endif
if BUILD_SYSTEMD
libcrmservice_la_SOURCES	+= systemd.c
endif
