CC=gcc
CXX=g++
OBJECTS=aaf.o afc.o instrument.o
CFLAGS=-g -O0 -Wall -Werror
CXXFLAGS=-std=c++14 -g -O0 -Wall -Werror -I/usr/local/include -I /opt/local/include
LDFLAGS=-g -lphosg -lphosg-audio -L/usr/local/lib -L/opt/local/lib
EXECUTABLES=smsdumpbanks smssynth
LIBS=-lphosg -lphosg-audio -lsamplerate

UNAME = $(shell uname -s)
ifeq ($(UNAME),Darwin)
	CXXFLAGS += -DMACOSX -I/opt/local/include
	LDFLAGS += -framework OpenAL -framework Cocoa -framework IOKit
endif
ifeq ($(UNAME),Linux)
	CXXFLAGS += -DLINUX
	LDFLAGS += -L/usr/lib/x86_64-linux-gnu
	LIBS += -lopenal -lpthread
endif


all: $(EXECUTABLES)

smsdumpbanks: $(OBJECTS) smsdumpbanks.o
	g++ $(LDFLAGS) -o smsdumpbanks $^ $(LIBS)

smssynth: $(OBJECTS) smssynth.o
	g++ $(LDFLAGS) -o smssynth $^ $(LIBS)

clean:
	-rm -rf *.o $(EXECUTABLES) *.dSYM

.PHONY: clean
