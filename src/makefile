.PHONY: clean zlib jpeg ogg vorbis freetype sdl sdl_ttf sdl_image sdl_mixer

OS := $(OSTYPE)
OS := $(OS:darwin%=darwin)
OS := $(OS:linux%=linux)
OS := $(OS:Linux%=linux)
OS := $(OS:Windows%=windows)

LIB_EXT := .a

ifeq ("$(OS)","darwin")
  SS_MAC := 1
  LIB_DIR := ../lib/mac
  JCONFIG := jconfig.mac
endif

ifeq ("$(OS)","iphone")
  SS_IPHONE := 1
  LIB_DIR := ../lib/iphone
  JCONFIG := jconfig.mac
endif

ifeq ("$(OS)","linux")
  SS_LINUX := 1
  LIB_DIR := ../lib/linux
  JCONFIG := jconfig.mac
endif

ifeq ("$(OS)","windows")
  SS_WINDOWS := 1
  LIB_DIR := ../lib/windows
  LIB_EXT := .lib
  JCONFIG := jconfig.vc
endif


all: zlib png jpeg ogg vorbis freetype sdl sdl_ttf sdl_image sdl_mixer

# --- ZLIB ------------------------
ZLIB := zlib-1.2.3

zlib:$(ZLIB)

$(ZLIB):
	tar xvzf tars/$(ZLIB).tgz
ifdef SS_WINDOWS
	cd $(ZLIB); unset MAKEFLAGS; nmake -f win32/Makefile.msc
	cp $(ZLIB)/zlib$(LIB_EXT) $(LIB_DIR)
else
	cd $(ZLIB); make
	cp $(ZLIB)/libz$(LIB_EXT) $(LIB_DIR)
endif
	cp $(ZLIB)/zlib.h $(ZLIB)/zconf.h ../include

clean::
	rm -rf $(ZLIB)

# --- PNG ------------------------

PNG := libpng-1.2.24

png:$(PNG)

$(PNG):
	tar xvzf tars/$(PNG).tgz
ifdef SS_WINDOWS
	cp configs/png-nmake-win32 $(PNG)/makefile
	cd $(PNG); unset MAKEFLAGS; nmake -f makefile
else
	cp configs/png-nmake-gcc $(PNG)/makefile
	cd $(PNG); make -f makefile
endif
	cp $(PNG)/libpng$(LIB_EXT) $(LIB_DIR)
	cp $(PNG)/png.h $(PNG)/pngconf.h ../include

clean::
	rm -rf $(PNG)

# --- JPEG ------------------------

JPEG := jpeg-6b

jpeg:$(JPEG)

$(JPEG):
	tar xvzf tars/$(JPEG).tgz
	cp $(JPEG)/$(JCONFIG) $(JPEG)/jconfig.h
ifdef SS_WINDOWS
	cd $(JPEG); unset MAKEFLAGS; nmake -f makefile.vc nodebug=1
else
	cd $(JPEG); ./configure
	cd $(JPEG); make -f makefile.unix nodebug=1
endif
	cp $(JPEG)/jpeglib.h $(JPEG)/jconfig.h $(JPEG)/jmorecfg.h ../include
	cp $(JPEG)/libjpeg$(LIB_EXT) $(LIB_DIR)

clean::
	rm -rf $(JPEG)

# --- OGG ------------------------

OGG := libogg-1.1.3

ogg:$(OGG)

$(OGG):
	tar xvzf tars/$(OGG).tgz
	cd $(OGG); ./configure
	cd $(OGG); make
	cp $(OGG)/src/.libs/libogg.a $(LIB_DIR)
	mkdir -p ../include/ogg
	cp $(OGG)/include/ogg/ogg.h ../include/ogg
	cp $(OGG)/include/ogg/config_types.h ../include/ogg
	cp $(OGG)/include/ogg/os_types.h ../include/ogg

clean::
	rm -rf $(OGG)


# --- VORBIS ------------------------

VORBIS := libvorbis-1.2.0

vorbis:$(VORBIS)

$(VORBIS):
	tar xvzf tars/$(VORBIS).tgz
	cp configs/vorbis-makefile $(VORBIS)/Makefile
	cd $(VORBIS); make
	cp $(VORBIS)/libvorbis.a $(LIB_DIR)
	mkdir -p ../include/vorbis
	cp $(VORBIS)/include/vorbis/vorbisfile.h ../include/vorbis
	cp $(VORBIS)/include/vorbis/codec.h ../include/vorbis
	cp $(VORBIS)/include/vorbis/vorbisenc.h ../include/vorbis

clean::
	rm -rf $(VORBIS)


# --- FREETYPE ------------------------

FREETYPE := freetype-2.3.9

freetype:$(FREETYPE)

$(FREETYPE):
	tar xvzf tars/$(FREETYPE).tgz
	cd $(FREETYPE); make
	cd $(FREETYPE); make
	cp $(FREETYPE)/objs/libfreetype.a $(LIB_DIR)
	cp $(FREETYPE)/include/ft2build.h ../include
	cp -r $(FREETYPE)/include/freetype ../include

clean::
	rm -rf $(FREETYPE)

# --- SDL ------------------------

SDL := SDL-1.3.0-4563

sdl:$(SDL)

$(SDL):
	tar xvzf tars/$(SDL).tgz
	cd $(SDL); ./configure --enable-shared=no
	cd $(SDL); make
	cp $(SDL)/build/.libs/libSDL.a $(LIB_DIR)
	cp $(SDL)/build/libSDLmain.a $(LIB_DIR)
	cp $(SDL)/include/*.h ../include

clean::
	rm -rf $(SDL)

# --- SDL_TTF ------------------------

SDL_TTF := SDL_ttf-2.0.9

sdl_ttf:$(SDL_TTF)

$(SDL_TTF):
	tar xvzf tars/$(SDL_TTF).tgz
	cp configs/sdl_ttf-makefile $(SDL_TTF)/Makefile
	cd $(SDL_TTF); make
	cp $(SDL_TTF)/libSDL_ttf.a $(LIB_DIR)
	cp $(SDL_TTF)/SDL_ttf.h ../include

clean::
	rm -rf $(SDL_TTF)

# --- SDL_IMAGE ------------------------

SDL_IMAGE := SDL_image-1.2.7

sdl_image:$(SDL_IMAGE)

$(SDL_IMAGE):
	tar xvzf tars/$(SDL_IMAGE).tgz
	cp configs/sdl_image-makefile $(SDL_IMAGE)/Makefile
	cd $(SDL_IMAGE); make
	cp $(SDL_IMAGE)/libSDL_image.a $(LIB_DIR)
	cp $(SDL_IMAGE)/SDL_image.h ../include

clean::
	rm -rf $(SDL_IMAGE)


# --- SDL_MIXER ------------------------

SDL_MIXER := SDL_mixer-1.2.8

sdl_mixer:$(SDL_MIXER)

$(SDL_MIXER):
	tar xvzf tars/$(SDL_MIXER).tgz
	cp configs/sdl_mixer-makefile $(SDL_MIXER)/Makefile
	cp patches/SDL_mixer/* $(SDL_MIXER)
	cd $(SDL_MIXER); make
	cp $(SDL_MIXER)/libSDL_mixer.a $(LIB_DIR)
	cp $(SDL_MIXER)/SDL_mixer.h ../include

clean::
	rm -rf $(SDL_MIXER)




