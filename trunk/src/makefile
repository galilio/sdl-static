.PHONY: clean zlib jpeg ogg vorbis

all: zlib png jpeg ogg vorbis

# --- ZLIB ------------------------
ZLIB := zlib-1.2.3

zlib:$(ZLIB)

$(ZLIB):
	tar xvzf tars/$(ZLIB).tgz
	cd $(ZLIB); unset MAKEFLAGS; nmake -f win32/Makefile.msc
	cp $(ZLIB)/zlib.h $(ZLIB)/zconf.h ../include
	cp $(ZLIB)/zlib.lib ../lib/win32

clean::
	rm -rf $(ZLIB)

# --- PNG ------------------------

PNG := libpng-1.2.24

png:$(PNG)

$(PNG):
	tar xvzf tars/$(PNG).tgz
	cp configs/png-nmake-win32 $(PNG)/makefile
	cd $(PNG); unset MAKEFLAGS; nmake -f makefile
	cp $(PNG)/png.h $(PNG)/pngconf.h ../include
	cp $(PNG)/libpng.lib ../lib/win32

clean::
	rm -rf $(PNG)

# --- JPEG ------------------------

JPEG := jpeg-6b

jpeg:$(JPEG)

$(JPEG):
	tar xvzf tars/$(JPEG).tgz
	cp $(JPEG)/jconfig.vc $(JPEG)/jconfig.h
	cd $(JPEG); unset MAKEFLAGS; nmake -f makefile.vc nodebug=1
	cp $(JPEG)/jpeglib.h $(JPEG)/jconfig.h $(JPEG)/jmorecfg.h ../include
	cp $(JPEG)/libjpeg.lib ../lib/win32

clean::
	rm -rf $(JPEG)

# --- JPEG ------------------------

JPEG := jpeg-6b

jpeg:$(JPEG)

$(JPEG):
	tar xvzf tars/$(JPEG).tgz
	cp $(JPEG)/jconfig.vc $(JPEG)/jconfig.h
	cd $(JPEG); unset MAKEFLAGS; nmake -f makefile.vc nodebug=1
	cp $(JPEG)/jpeglib.h $(JPEG)/jconfig.h $(JPEG)/jmorecfg.h ../include
	cp $(JPEG)/libjpeg.lib ../lib/win32

clean::
	rm -rf $(JPEG)


