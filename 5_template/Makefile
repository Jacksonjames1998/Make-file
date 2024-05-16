#TARGETS
#target: prerequisite

# Note: variable can only be strings
# NOte: any double or single quotes for variable name or value have no meaning in make

DEBUG = 1
INCLUDE_WARNINGS = 1
WARNING_AS_ERROR = 0
INCLUDE_DIR = include
SRC_DIR = src
BUILD_DIR = build

EXECUTABLE_NAME = main
CXX_STANDARD = c++17
CXX = g++
CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)
LDFLAGS = -lmath

CPPFLAGS = -I $(INCLUDE_DIR)

CXX_COMPILER_CALL = $(CXX) $(CXXFLAGS) $(CPPFLAGS)

ifeq ($(INCLUDE_WARNINGS),1)
CXX_WARNINGS = -Wall -Wextra -Wpedantic
else
CXX_WARNINGS =
endif

ifeq ($(WARNING_AS_ERROR),1)
CXX_WARNINGS += -Werror
endif


ifeq ($(DEBUG),1)
CXXFLAGS += -g -O0
EXECUTABLE_NAME = mainDebug
else
CXXFLAGS += -O3
EXECUTABLE_NAME = mainRelease
endif

CXX_SOURCES = $(wildcard $(SRC_DIR)/*.cpp)
CXX_OBJECTS = $(patsubst $(SRC_DIR)/%.cpp, $(SRC_DIR)/%.o, $(CXX_SOURCES))

create:
	mkdir $(BUILD_DIR)

build: create $(CXX_OBJECTS)
	$(CXX_COMPILER_CALL) $(CXX_OBJECTS) -o $(BUILD_DIR)/$(EXECUTABLE_NAME)
	echo $(CXX_SOURCES)
	echo $(CXX_OBJECTS)

execute:
	./$(BUILD_DIR)/$(EXECUTABLE_NAME)

clean:
	rm -f $(BUILD_DIR)/*.o
	rm -f $(BUILD_DIR)/$(EXECUTABLE_NAME)

#PATTERNS
#$@ - the file name of the target
#$< - name of the first dependency
#$^ - name of the all prerequisite

$(BUILD_DIR)%.o: $(SRC_DIR)%.cpp
	$(CXX_COMPILER_CALL) -c $< -o $@

#PHONY -targets do not corresponds to any file name

.PHONY: create build execute clean