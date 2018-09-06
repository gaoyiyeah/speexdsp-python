

SWIG := swig

# PY_CONFIG := $(shell python-config --cflags)
PY_CONFIG := -I/System/Library/Frameworks/Python.framework/Versions/2.7/include/python2.7 -I/System/Library/Frameworks/Python.framework/Versions/2.7/include/python2.7 -fno-strict-aliasing -fno-common -dynamic -arch x86_64 -g -Os -pipe -fno-common -fno-strict-aliasing -fwrapv -DENABLE_DTRACE -DMACOSX -DNDEBUG -Wall -Wstrict-prototypes -Wshorten-64-to-32 -DNDEBUG -g -fwrapv -Os -Wall -Wstrict-prototypes -DENABLE_DTRACE
CXXFLAGS :=  -fPIC -std=c++11 -I. $(shell pkg-config --cflags speexdsp)  $(PY_CONFIG)
LDFLAGS := -shared $(shell pkg-config --libs speexdsp) $(shell python-config --ldflags)
CXX := g++


all: _speexdsp.so

speexdsp_wrap.cpp: speexdsp.i
	$(SWIG) -I. -c++ -python -o $@ $^

_speexdsp.so: speexdsp_wrap.o echo_canceller.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) -o $@ $^

clean:
	-rm -f speexdsp_wrap.cpp *.o _speexdsp.so speexdsp.py *.pyc 
