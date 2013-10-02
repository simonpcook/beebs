#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([beebs], [1.0], [james.pallister@embecosm.com])
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_AUX_DIR([build-aux])

AC_CANONICAL_SYSTEM

AM_INIT_AUTOMAKE
AC_PROG_LIBTOOL
LT_INIT
AC_CONFIG_SRCDIR([src/])
#AC_CONFIG_HEADERS([config.h])

host=arm-none-eabi

if test x$host == x$build ; then
    cross_compiling=no
else
    cross_compiling=yes
fi

AC_PROG_CC_C99

if test x$cross_compiling == xyes ; then
    # Check that the specified cross compiler exists
    AC_CHECK_PROG(CROSS_COMPILER_CHECK,$host-gcc,yes,no)

    if test x"${CROSS_COMPILER_CHECK}" == x"no" ; then
        AC_MSG_ERROR([Cannot find $host-gcc])
    fi
fi

AC_ARG_WITH([linkerscript],
            [AS_HELP_STRING([--with-linkerscript],
              [Choose the linker script])],
            [],
            [with_linkerscript=no])

echo $with_linkerscript
if test x$with_linkerscript == xno ; then
    with_linkerscript=""
else
    lk=`readlink -m ${with_linkerscript}`
#    with_linkerscript="-T ${lk}"
    AC_SUBST([LINKERSCRIPT], ["-T ${lk}"])
fi

echo $with_linkerscript

AC_CONFIG_FILES([src/2dfir/Makefile])
AC_CONFIG_FILES([src/blowfish/Makefile])
AC_CONFIG_FILES([src/crc32/Makefile])
AC_CONFIG_FILES([src/cubic/Makefile])
AC_CONFIG_FILES([src/dijkstra/Makefile])
AC_CONFIG_FILES([src/fdct/Makefile])
AC_CONFIG_FILES([src/float_matmult/Makefile])
AC_CONFIG_FILES([src/int_matmult/Makefile])
AC_CONFIG_FILES([src/rijndael/Makefile])
AC_CONFIG_FILES([src/sha/Makefile])
AC_CONFIG_FILES([Makefile src/common.mk])
AC_OUTPUT