#
#  Licensed to the Apache Software Foundation (ASF) under one
#  or more contributor license agreements.  See the NOTICE file
#  distributed with this work for additional information
#  regarding copyright ownership.  The ASF licenses this file
#  to you under the Apache License, Version 2.0 (the
#  "License"); you may not use this file except in compliance
#  with the License.  You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
#  Unless required by applicable law or agreed to in writing, software
#  distributed under the License is distributed on an "AS IS" BASIS,
#  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#  See the License for the specific language governing permissions and
#  limitations under the License.

# We only build tstop if libcurses and libcurl are available.
if BUILD_TSTOP

bin_PROGRAMS = traffic_top

AM_CPPFLAGS = $(iocore_include_dirs) \
  -I$(top_srcdir)/lib -I$(top_builddir)/lib \
  -I$(top_srcdir)/lib/ts -I$(top_builddir)/lib/ts

traffic_top_CPPFLAGS = \
  -I$(top_srcdir)/mgmt/api/include
traffic_top_CXXFLAGS = \
  @CURL_CFLAGS@

traffic_top_SOURCES = traffic_top.cc
traffic_top_LDADD = \
  $(top_builddir)/mgmt/api/libtsmgmtshare.la \
  $(top_builddir)/mgmt/api/libtsmgmt.la \
  @CURL_LIBS@ @CURSES_LIB@

# Install a compatibility symlink because traffic_top was named tstop in previous releases.
install-exec-hook:
	cd $(DESTDIR)$(bindir) && $(RM) tstop && $(LN_S) traffic_top tstop
endif
