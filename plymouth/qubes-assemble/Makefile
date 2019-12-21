ALL = $(patsubst %.svg,%.png,$(wildcard *.svg)) lock.png

all: $(ALL)
.PHONY: all


# progress-* and throbber-* created with:
# animation in PowerPoint, black background, 1280x720, exported to mp4, then:
# 1. Splint into png files:
#   mplayer -vo png Presentation1.mp4
# 2. Extract progress-*:
#   for x in `seq 0 19`; do convert -crop 470x470+308+135 -transparent black -fuzz 40%  $(printf %08d $((x*3+1))).png progress-$(printf %02d $x).png; done
# 3. Extract throbber-*:
#   for x in `seq 0 15`; do convert -crop 470x470+308+135 -transparent black -fuzz 20%  $(printf %08d $((x*3+60))).png throbber-$(printf %02d $x).png; done


%.png: %.svg
	convert -background none -antialias $< $@
#	inkscape --export-png=$@ $<

lock.png:
	../../bin/mkpadlock.py -s 40 -c 0xee0000 $@

clean:
	$(RM) $(ALL)
.PHONY: clean

install:
	mkdir -p $(DESTDIR)/usr/share/plymouth/themes/qubes-assemble
	install -m 0644 -t $(DESTDIR)/usr/share/plymouth/themes/qubes-assemble \
		$(ALL) \
		bullet.png \
		entry.png \
		box.png \
		qubes-assemble.plymouth \
		progress-*.png \
		throbber-*.png

.PHONY: install
