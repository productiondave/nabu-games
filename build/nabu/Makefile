
TOP=../..

# Name each subdir to build before making the filesystem
SUBDIRS=\
	tetris \
	snake \
	invaders \
	imagui

.PHONY: c.dsk all store

# make 'all' be the default build target...
all::

include Make.rules

# ...but don't try to make the disk image until after the subdirs are done!
all:: copy

# make sure all subdirs are built before we make the disk image
copy: $(ALL_DIRS)
	find . -name "*.com" -exec cp -fv {} $(STOREDIR)/ \;

clean::
	rm -f c.dsk

release: $(ALL_DIRS)
	@if [ -e $(GIT_TAG) ]; then echo "\n\n** ERROR: you have not tagged this commit!\n\n"; exit 1; fi
	tar -c -z -v -f  nabu-games-$(GIT_TAG).tgz snake/SNAKE.COM snake/000001.NABU tetris/TETRIS.COM tetris/000001.NABU invaders/INVADERS.COM invaders/000001.NABU
	zip  -r -v  nabu-games-$(GIT_TAG).zip snake/SNAKE.COM snake/000001.NABU tetris/TETRIS.COM tetris/000001.NABU invaders/INVADERS.COM invaders/000001.NABU
