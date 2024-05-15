#TARGETS
#target: prerequisite

# Note: variable can only be strings
# NOte: any double or single quotes for variable name or value have no meaning in make

DEBUG = 1
EXECUTABLE_NAME = main
CXX_STANDARD = c++17
CXX_WARNINGS = -Wall -Wextra -Wpedantic
CXX = g++
CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)
LDFLAGS = -lmath

COMPILER_CALL = $(CXX) $(CXXFLAGS)

ifeq ($(DEBUG),1)
CXXFLAGS += -g -O0
else
CXXFLAGS += -O3
endif

build: mylib.o main.o
	$(COMPILER_CALL) main.o mylib.o -o bin/$(EXECUTABLE_NAME)

main.o:
	$(COMPILER_CALL) main.cpp -c
mylib.o:
	$(COMPILER_CALL) mylib.cpp -c

execute:
	./bin/main

clean:
	rm -f *.o
	rm -f main