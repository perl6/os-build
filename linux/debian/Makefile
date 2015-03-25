.PHONY: help moarvm nqp rakudo clean

help:
	@echo "Possible make targets: all, moarvm, nqp, rakudo, clean"

all: moarvm nqp rakudo

moarvm:
	cd moarvm/; $(MAKE) deb

nqp:
	cd nqp/; $(MAKE) deb

rakudo:
	cd rakudo/; $(MAKE) deb

clean:
	for dir in moarvm nqp rakudo;\
	do\
	    cd $$dir; $(MAKE) clean;\
	    cd ..;\
	done
