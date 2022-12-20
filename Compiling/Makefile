SUBDIRS = Ubuntu-20.04 Ubuntu-22.04


CLEANFILES = *~



all:
	for d in $(SUBDIRS) ; do make -C $$d build run ; done


clean:
	for d in $(SUBDIRS) ; do make -C $$d clean ; done
	rm -f $(CLEANFILES)
