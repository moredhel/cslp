# -Wall -save-temps -Wshadow -fmudflap
CC=gcc
CFLAGS=-pipe -m64 -ansi -fPIC -g -O3 -fno-exceptions -fstack-protector -fvisibility=hidden -W -Wall -Wno-unused-parameter -Wno-unused-function -Wno-unused-label -Wpointer-arith -Wformat -Wreturn-type -Wsign-compare -Wmultichar -Winit-self -Wuninitialized -Wno-deprecated -Wformat-security -Werror -std=gnu99 -D DEBUG -c
LDFLAGS=-lm -L/usr/local/lib

CPATH="/usr/local/lib:/usr/local/include:../lib/"
MAIN_SOURCES= $(shell cat ../src/files.txt)
SOURCES= \
$(shell cat ../deps.txt) \
$(addprefix ../src/, $(MAIN_SOURCES)) \
$(shell cat files.txt)

OBJECTS=$(SOURCES:.c=.o)
EXECUTABLE=../bin/cslp-test

all: $(SOURCES) $(EXECUTABLE)

$(EXECUTABLE): $(OBJECTS)
	@$(CC) $(LDFLAGS) $(OBJECTS) -o $@

.c.o:
	@CPATH=$(CPATH) $(CC) $(CFLAGS) $< -o $@

clean:
	rm $(EXECUTABLE) $(OBJECTS)
