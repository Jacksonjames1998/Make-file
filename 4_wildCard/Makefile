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

CXX_COMPILER_CALL = $(CXX) $(CXXFLAGS)

ifeq ($(DEBUG),1)
CXXFLAGS += -g -O0
EXECUTABLE_NAME = mainDebug
else
CXXFLAGS += -O3
EXECUTABLE_NAME = mainRelease
endif

CXX_SOURCES = $(wildcard *.cpp)
CXX_OBJECTS = $(patsubst %.cpp, %.o, $(CXX_SOURCES))
build: $(CXX_OBJECTS)
	$(CXX_COMPILER_CALL) $(CXX_OBJECTS) -o bin/$(EXECUTABLE_NAME)
	echo $(CXX_SOURCES)
	echo $(CXX_OBJECTS)

# main.o:
# 	$(CXX_COMPILER_CALL) main.cpp -c
# mylib.o:
# 	$(CXX_COMPILER_CALL) mylib.cpp -c

execute:
	./bin/$(EXECUTABLE_NAME)

clean:
	rm -f *.o
	rm -f bin/$(EXECUTABLE_NAME)

#PATTERNS
#$@ - the file name of the target
#$< - name of the first dependency
#$^ - name of the all prerequisite

%.o: %.cpp
	$(CXX_COMPILER_CALL) -c $< -o $@