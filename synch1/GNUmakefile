PROGRAMS = threadex1 threadex2 threadex3 threadref threadjoin \
	threadstack \
	incr-atomic incr-basic incr-basic-noopt incr-mutex \
	incr-scopedlock incr-spinlock incr-spinlock2 \
	incr-trymutex incr-volatile incr-atomicbad \
	spinlock-fairness

all: $(PROGRAMS)

ALLPROGRAMS = $(PROGRAMS)
CONFIGMK ?= config.mk

O ?= 3
PTHREAD ?= 1
include ../common/rules.mk
-include $(CONFIGMK)

%.o: %.cc $(BUILDSTAMP)
	$(CXX) $(CPPFLAGS) $(CXXFLAGS) $(DEPCFLAGS) $(O) -o $@ -c $<

%-noopt.o: %.cc $(BUILDSTAMP)
	$(CXX) $(CPPFLAGS) $(CXXFLAGS) $(DEPCFLAGS) -O0 -o $@ -c $<

$(PROGRAMS): \
%: %.o print_bytes.o
	$(CXX) $(CXXFLAGS) $(O) $(LDFLAGS) -o $@ $^ $(LIBS)


clean:
	rm -f $(ALLPROGRAMS) *.o
	rm -rf $(DEPSDIR) *.dSYM

.PHONY: all always clean
