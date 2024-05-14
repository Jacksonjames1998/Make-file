#TARGETS
#target: prerequisite

build: mylib.o main.o
	g++ main.o mylib.o -o main

main.o:
	g++ main.cpp -c
mylib.o:
	g++ mylib.cpp -c

execute:
	./main

clean:
	rm -f *.o
	rm -f main