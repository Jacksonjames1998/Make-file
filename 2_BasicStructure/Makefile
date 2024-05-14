#TARGETS
#target: prerequisite

build: mylib.o main.o
	g++ main.o mylib.o -o bin/main

main.o:
	g++ main.cpp -c
mylib.o:
	g++ mylib.cpp -c

execute:
	./bin/main

clean:
	rm -f *.o
	rm -f main