#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ(2.59)
AC_INIT([besm6], [2.5], [http://groups.google.com/group/besm6/topics])
#AM_INIT_AUTOMAKE(besm6, 2.5, no-define)
AC_CONFIG_SRCDIR([dispak/extra.c])
AM_INIT_AUTOMAKE([subdir-objects])
AC_CONFIG_HEADER([config.h])
AC_CONFIG_FILES([Makefile dispak/Makefile po/Makefile.in])
AC_CONFIG_FILES([besmtool/Makefile disbesm6/Makefile])

# Checks for programs.
AC_PROG_CC
AC_PROG_YACC

# Checks for libraries.
if test -d /opt/local; then
	CFLAGS="$CFLAGS -I/opt/local/include"
	LDFLAGS="$LDFLAGS -L/opt/local/lib"
fi
AC_CHECK_LIB([m], [sin])
AC_CHECK_LIB([sunmath], [isinf])
AC_CHECK_LIB([rt], [clock_getres])
AC_CHECK_LIB([readline], [readline], [READLINE_LIB=-lreadline])
AC_CHECK_LIB([SDL2_ttf], [TTF_Init])

if test ":$ac_cv_lib_SDL2_ttf_TTF_Init" != ":yes" ; then
AC_CHECK_LIB([SDL_ttf], [TTF_Init])
fi

AM_GNU_GETTEXT_VERSION([0.16])
AM_GNU_GETTEXT([external])
AM_CONDITIONAL(HAVE_READLINE, test ":$ac_cv_lib_readline_readline" = ":yes")
AM_CONDITIONAL(HAVE_LIBSDL2, test ":$ac_cv_lib_SDL2_ttf_TTF_Init" = ":yes")
AM_CONDITIONAL(HAVE_LIBSDL, test ":$ac_cv_lib_SDL_ttf_TTF_Init" = ":yes")

# Checks for header files.

# Checks for typedefs, structures, and compiler characteristics.
AC_C_CONST
AC_CHECK_TYPES([ulong])
AC_CHECK_TYPES([ushort])
AC_CHECK_TYPES([uint])
AC_C_BIGENDIAN
AC_TYPE_INT64_T
AC_TYPE_UINT64_T
AC_CHECK_SIZEOF([long])
AC_CHECK_SIZEOF([long long])

# Checks for library functions.
AC_CHECK_FUNCS(getopt_long)
AC_OUTPUT
