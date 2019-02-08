CXXFLAGS=-Wall -O3 -g
OBJECTS= pixel-test.o 
BINARIES= pixel-test

# Where our library resides. It is split between includes and the binary
# library in lib
RGB_INCDIR=../include
RGB_LIBDIR=../lib
RGB_LIBRARY_NAME=rgbmatrix
RGB_LIBRARY=$(RGB_LIBDIR)/lib$(RGB_LIBRARY_NAME).a
LDFLAGS+=-L$(RGB_LIBDIR) -l$(RGB_LIBRARY_NAME) -lrt -lm -lpthread

all : $(BINARIES)

$(RGB_LIBRARY): FORCE
	$(MAKE) -C $(RGB_LIBDIR)

pixel-test : pixel-test.o $(RGB_LIBRARY)
	$(CXX) $(CXXFLAGS) pixel-test.o -o $@ $(LDFLAGS)

pixel-test.o : pixel-test.cc
	$(CXX) -I$(RGB_INCDIR) $(CXXFLAGS) -c -o $@ $<

%.o : %.cc
	$(CXX) -I$(RGB_INCDIR) $(CXXFLAGS) -c -o $@ $<

clean:
	$(MAKE) -C lib clean

FORCE:
.PHONY: FORCE
