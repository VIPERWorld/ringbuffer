
LIBS = -pthread -lcheck_pic -pthread -lrt -lm -lsubunit
LIB_DIR=usr/lib
LDFLAGS=-L$(LIB_DIR) $(LIBS)

OBJDIR=.
CSOURCES = $(wildcard *.c)
CSOURCES += $(wildcard ../src/*.c)

CCOMPILER=gcc

all: test

test: $(CSOURCES:.c=.o)
	$(CCOMPILER) -o $@ $^ $(LDFLAGS)
	
%.o: %.c
	$(CCOMPILER) -c $< $(CFLAGS) -o $(OBJDIR)/$@

clean:
	-rm -f *.o tests *~

remade:
	$(MAKE) clean
	$(MAKE)

-include $(CSOURCES:.c:.d)

%.d: %.d
	gcc $< -MM -MT '$*.o $*.d' -MD $(CFLAGS)
