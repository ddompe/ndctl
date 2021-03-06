include $(top_srcdir)/Makefile.am.in

TESTS =\
	libndctl \
	dsm-fail \
	dpa-alloc \
	parent-uuid \
	multi-pmem \
	create.sh \
	clear.sh \
	dax-errors.sh

check_PROGRAMS =\
	libndctl \
	dsm-fail \
	dpa-alloc \
	parent-uuid \
	multi-pmem \
	dax-errors

if ENABLE_DESTRUCTIVE
TESTS +=\
	blk-ns \
	pmem-ns \
	dax-dev \
	dax.sh \
	device-dax \
	mmap.sh

check_PROGRAMS +=\
	blk-ns \
	pmem-ns \
	dax-dev \
	dax-pmd \
	device-dax \
	mmap
endif

LIBNDCTL_LIB =\
       ../ndctl/lib/libndctl.la \
       ../daxctl/lib/libdaxctl.la

libndctl_SOURCES = libndctl.c core.c
libndctl_LDADD = $(LIBNDCTL_LIB) $(UUID_LIBS) $(KMOD_LIBS)

dsm_fail_SOURCES =\
	dsm-fail.c \
	core.c \
	../util/log.c \
	../util/sysfs.c

dsm_fail_LDADD = $(LIBNDCTL_LIB) $(KMOD_LIBS)

blk_ns_SOURCES = blk_namespaces.c core.c
blk_ns_LDADD = $(LIBNDCTL_LIB) $(KMOD_LIBS)

pmem_ns_SOURCES = pmem_namespaces.c core.c
pmem_ns_LDADD = $(LIBNDCTL_LIB) $(KMOD_LIBS)

dpa_alloc_SOURCES = dpa-alloc.c core.c
dpa_alloc_LDADD = $(LIBNDCTL_LIB) $(UUID_LIBS) $(KMOD_LIBS)

parent_uuid_SOURCES = parent-uuid.c core.c
parent_uuid_LDADD = $(LIBNDCTL_LIB) $(UUID_LIBS) $(KMOD_LIBS)

dax_dev_SOURCES = dax-dev.c core.c
dax_dev_LDADD = $(LIBNDCTL_LIB)

dax_pmd_SOURCES = dax-pmd.c
mmap_SOURCES = mmap.c
dax_errors_SOURCES = dax-errors.c
device_dax_SOURCES = \
		device-dax.c \
		dax-dev.c \
		dax-pmd.c \
		core.c \
		../ndctl/builtin-xaction-namespace.c \
		../ndctl/util/json.c
device_dax_LDADD = \
		$(LIBNDCTL_LIB) \
		$(JSON_LIBS) \
		../libutil.a

multi_pmem_SOURCES = \
		multi-pmem.c \
		core.c \
		../ndctl/builtin-xaction-namespace.c \
		../ndctl/util/json.c
multi_pmem_LDADD = \
		$(LIBNDCTL_LIB) \
		$(JSON_LIBS) \
		../libutil.a
