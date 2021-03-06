#   Copyright (C) 2018-2020 Adam Leszczynski (aleszczynski@bersler.com)
#
#This file is part of OpenLogReplicator.
#
#OpenLogReplicator is free software; you can redistribute it and/or
#modify it under the terms of the GNU General Public License as published
#by the Free Software Foundation; either version 3, or (at your option)
#any later version.
#
#OpenLogReplicator is distributed in the hope that it will be useful,
#but WITHOUT ANY WARRANTY; without even the implied warranty of
#MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General
#Public License for more details.
#
#You should have received a copy of the GNU General Public License
#along with OpenLogReplicator; see the file LICENSE;  If not see
#<http://www.gnu.org/licenses/>.

AC_PREREQ(2.68)
AC_INIT([OpenLogReplicator],[0.7.17],[aleszczynski@bersler.com])
AC_USE_SYSTEM_EXTENSIONS
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_AUX_DIR(config)
AC_CONFIG_MACRO_DIR([m4])
AM_INIT_AUTOMAKE()

LT_INIT()
AC_PROG_CXX
AC_LANG([C++])
AC_FUNC_STRNLEN
AC_HEADER_STDC
AC_CHECK_HEADERS([fcntl.h unistd.h])
AC_FUNC_MALLOC
AC_FUNC_MKTIME
AC_CHECK_FUNCS([memset])
AC_CHECK_HEADER_STDBOOL
AC_TYPE_INT16_T
AC_TYPE_INT32_T
AC_TYPE_INT64_T
AC_TYPE_INT8_T
AC_TYPE_SIZE_T
AC_TYPE_UINT16_T
AC_TYPE_UINT32_T
AC_TYPE_UINT64_T
AC_TYPE_UINT8_T

AC_ARG_WITH([rdkafka],
  [AS_HELP_STRING([--with-rdkafka=PATH], [rdkafka directory])],
  [CPPFLAGS="-I$withval/include $CPPFLAGS -DLINK_LIBRARY_LIBRDKAFKA"; LDFLAGS="-L$withval/lib -lrdkafka++ -lrdkafka $LDFLAGS"]
  [])

AC_ARG_WITH([rapidjson],
  [AS_HELP_STRING([--with-rapidjson=PATH], [rapidjson directory])],
  [CPPFLAGS="-I$withval/include $CPPFLAGS"]
  [])

AC_ARG_WITH([grpc],
  [AS_HELP_STRING([--with-grpc=PATH], [grpc directory])],
  [PROTOBUF=true; CPPFLAGS="-I$withval/include -DLINK_LIBRARY_PROTOBUF -DLINK_LIBRARY_GRPC $CPPFLAGS"; LDFLAGS="-L$withval/lib -L$withval/lib64 `export PKG_CONFIG_PATH=$withval/lib/pkgconfig:$withval/lib64/pkgconfig; pkg-config --libs protobuf grpc++` $LDFLAGS"],
  [])

AC_ARG_WITH([instantclient],
  [AS_HELP_STRING([--with-instantclient=PATH], [instant client directory])],
  [CPPFLAGS="-I$withval/sdk/include -DLINK_LIBRARY_OCI $CPPFLAGS"; LDFLAGS="-L$withval -lclntshcore -lnnz19 -lclntsh $LDFLAGS"],
  [])

CXXFLAGS="$CXXFLAGS -std=c++0x -pedantic -pedantic-errors -w -Wall -Wextra -fmessage-length=0"
LDFLAGS="$LDFLAGS -pthread"
AM_CONDITIONAL([PROTOBUF_COMPILE], [test x$PROTOBUF = xtrue])

AC_CONFIG_FILES([
  Makefile 
  src/Makefile
])
AC_OUTPUT()

