CC = gcc
AR = ar
RANLIB = ranlib
CFLAGS = -std=c99 -g -Wall -Wextra -pedantic
EXE = .exe
LIBSFX = .a

all: libpnmio$(LIBSFX) randimg$(EXE) doset$(EXE)

libpnmio.a: pnmio.o
	$(AR) -q libpnmio$(LIBSFX) pnmio.o
	chmod 755 libpnmio$(LIBSFX)
	$(RANLIB) libpnmio$(LIBSFX)
	cp -f libpnmio$(LIBSFX) ../lib
	rm -f libpnmio$(LIBSFX)

randimg$(EXE): randimg.o
	$(CC) randimg.o ../lib/libpnmio.a $(LFLAGS) -o randimg$(EXE)
	mv randimg$(EXE) ../bin

doset$(EXE): doset.o
	$(CC) doset.o ../lib/libpnmio.a $(LFLAGS) -o doset$(EXE)
	mv doset$(EXE) ../bin

pnmio.o: pnmio.c pnmio.h
	$(CC) $(CFLAGS) -c pnmio.c $(INCLUDES)

randimg.o: randimg.c pnmio.h
	$(CC) $(CFLAGS) $(INCLUDES) -c randimg.c

doset.o: doset.c pnmio.h
	$(CC) $(CFLAGS) $(INCLUDES) -c doset.c
   
tidy:
	rm -f *.o

clean:
	rm -f *.o ../lib/libpnmio$(LIBSFX) ../bin/randimg$(EXE) ../bin/doset$(EXE)