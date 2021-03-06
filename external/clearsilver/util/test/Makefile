

ifeq ($(NEOTONIC_ROOT),)
NEOTONIC_ROOT = ../../
endif

include $(NEOTONIC_ROOT)rules.mk

HDFTEST_EXE = hdftest
HDFTEST_SRC = hdftest.c
HDFTEST_OBJ = $(HDFTEST_SRC:%.c=%.o)

HDFSORTTEST_EXE = hdf_sort_test
HDFSORTTEST_SRC = hdf_sort_test.c
HDFSORTTEST_OBJ = $(HDFSORTTEST_SRC:%.c=%.o)

HDFLOADTEST_EXE = hdfloadtest
HDFLOADTEST_SRC = hdfloadtest.c
HDFLOADTEST_OBJ = $(HDFLOADTEST_SRC:%.c=%.o)

LISTDIRTEST_EXE = listdir_test
LISTDIRTEST_SRC = listdir_test.c
LISTDIRTEST_OBJ = $(LISTDIRTEST_SRC:%.c=%.o)

HDFCOPYTEST_EXE = hdf_copy_test
HDFCOPYTEST_SRC = hdf_copy_test.c
HDFCOPYTEST_OBJ = $(HDFCOPYTEST_SRC:%.c=%.o)

HDFDEALLOCTEST_EXE = hdf_dealloc_test
HDFDEALLOCTEST_SRC = hdf_dealloc_test.c
HDFDEALLOCTEST_OBJ = $(HDFDEALLOCTEST_SRC:%.c=%.o)

NETTEST_EXE = net_test
NETTEST_SRC = net_test.c
NETTEST_OBJ = $(NETTEST_SRC:%.c=%.o)

DATETEST_EXE = date_test
DATETEST_SRC = date_test.c
DATETEST_OBJ = $(DATETEST_SRC:%.c=%.o)

HASHTEST_EXE = hash_test
HASHTEST_SRC = hash_test.c
HASHTEST_OBJ = $(HASHTEST_SRC:%.c=%.o)

ULISTTEST_EXE = ulist_test
ULISTTEST_SRC = ulist_test.c
ULISTTEST_OBJ = $(ULISTTEST_SRC:%.c=%.o)

CFLAGS += -I$(NEOTONIC_ROOT)/util
LIBS += -lneo_utl 

TARGETS = $(HDFTEST_EXE) $(LISTDIRTEST_EXE) $(HDFCOPYTEST_EXE) \
	$(HDFSORTTEST_EXE) $(HDFDEALLOCTEST_EXE) \
	$(HDFLOADTEST_EXE) $(NETTEST_EXE) $(DATETEST_EXE) \
	$(HASHTEST_EXE) $(ULISTTEST_EXE)

all: $(TARGETS)

$(ULISTTEST_EXE): $(ULISTTEST_OBJ) $(NTR_LIB)
	$(LD) $@ $(ULISTTEST_OBJ) $(LDFLAGS) $(LIBS)

$(HDFTEST_EXE): $(HDFTEST_OBJ) $(NTR_LIB)
	$(LD) $@ $(HDFTEST_OBJ) $(LDFLAGS) $(LIBS)

$(HDFSORTTEST_EXE): $(HDFSORTTEST_OBJ) $(NTR_LIB)
	$(LD) $@ $(HDFSORTTEST_OBJ) $(LDFLAGS) $(LIBS)

$(HDFDEALLOCTEST_EXE): $(HDFDEALLOCTEST_OBJ) $(NTR_LIB)
	$(LD) $@ $(HDFDEALLOCTEST_OBJ) $(LDFLAGS) $(LIBS)

$(HDFLOADTEST_EXE): $(HDFLOADTEST_OBJ) $(NTR_LIB)
	$(LD) $@ $(HDFLOADTEST_OBJ) $(LDFLAGS) $(LIBS) # -lefence

$(LISTDIRTEST_EXE): $(LISTDIRTEST_OBJ) $(NTR_LIB)
	$(LD) $@ $(LISTDIRTEST_OBJ) $(LDFLAGS) $(LIBS)

$(HDFCOPYTEST_EXE): $(HDFCOPYTEST_OBJ) $(NTR_LIB)
	$(LD) $@ $(HDFCOPYTEST_OBJ) $(LDFLAGS) $(LIBS) # -lefence

$(NETTEST_EXE): $(NETTEST_OBJ) $(NTR_LIB)
	$(LD) $@ $(NETTEST_OBJ) $(LDFLAGS) $(LIBS)

$(DATETEST_EXE): $(DATETEST_OBJ) $(NTR_LIB)
	$(LD) $@ $(DATETEST_OBJ) $(LDFLAGS) $(LIBS)

$(HASHTEST_EXE): $(HASHTEST_OBJ) $(NTR_LIB)
	$(LD) $@ $(HASHTEST_OBJ) $(LDFLAGS) $(LIBS) # -lefence

clean:
	$(RM) *.o

distclean:
	$(RM) $(TARGETS) *.o
