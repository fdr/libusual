
AM_FEATURES = libusual

SUBLOC = test
DIST_SUBDIRS = attregex

USUAL_DIR = $(abs_top_srcdir)

regtest_system_SOURCES = \
	test_string.c test_crypto.c test_aatree.c test_heap.c \
	test_common.c test_list.c tinytest.c test_cbtree.c \
	test_utf8.c test_strpool.c test_pgutil.c test_regex.c \
	test_cxalloc.c test_bits.c test_base.c test_netdb.c \
	test_cfparser.c test_endian.c test_hashtab.c test_mdict.c \
	test_shlist.c test_time.c test_hashing.c test_fileutil.c \
	test_socket.c test_getopt.c test_ctype.c \
	test_common.h tinytest.h tinytest_macros.h

regtest_compat_SOURCES := $(regtest_system_SOURCES)
nodist_regtest_compat_SOURCES = test_config.h

regtest_compat_EMBED_LIBUSUAL = 1
regtest_system_EMBED_LIBUSUAL = 1

regtest_system_LDADD = -lanl
regtest_system_LDFLAGS = -pthread

regtest_system_CPPFLAGS = -I.. -I.
regtest_compat_CPPFLAGS := $(regtest_system_CPPFLAGS) -DUSUAL_TEST_CONFIG
regtest_compat_LDFLAGS = -pthread

EXTRA_DIST = Makefile tinytest_demo.c force_compat.sed test_cfparser.ini

noinst_PROGRAMS = regtest_system regtest_compat

include ../build.mk

test_config.h: force_compat.sed ../usual/config.h
	$(E) "	GEN-COMPAT" $@
	$(Q) sed -f $^ > $@

