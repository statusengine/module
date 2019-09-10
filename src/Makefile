all: bin/nagios/statusengine.o bin/naemon/statusengine.o bin/naemon/statusengine-1-0-5.o bin/naemon/statusengine-1-1-0.o

bin/nagios/statusengine.o: statusengine.c
	mkdir -p bin/nagios
	LANG=C gcc -DNAGIOS -shared -o "$@" -fPIC  -Wall -Werror statusengine.c -luuid -levent -lgearman -ljson-c

bin/naemon/statusengine.o: statusengine.c
	mkdir -p bin/naemon
	LANG=C gcc -DNAEMON -shared -o "$@" -fPIC  -Wall -Werror statusengine.c -luuid -levent -lgearman -ljson-c


bin/naemon/statusengine-1-0-5.o: statusengine.c
	mkdir -p bin/naemon
	LANG=C gcc `pkg-config --cflags --libs glib-2.0` -DNAEMON105 -shared -o "$@" -fPIC  -Wall -Werror statusengine.c -luuid -levent -lgearman -ljson-c -lglib-2.0

bin/naemon/statusengine-1-1-0.o: statusengine.c
	mkdir -p bin/naemon
	LANG=C gcc `pkg-config --cflags --libs glib-2.0` -DNAEMON110 -shared -o "$@" -fPIC  -Wall -Werror statusengine.c -luuid -levent -lgearman -ljson-c -lglib-2.0

clean:
	rm -f bin/nagios/statusengine.o bin/naemon/statusengine.o bin/naemon/statusengine-1-0-5.o
