---------------------------
      HOW TO BUILD
---------------------------


For most targets, go to the /src directory, then run "make OS=platform"

Supported platforms include:

 - windows
 - darwin (Mac)
 - linux
 - webos
 - blackberry
 - android
 - iphoneos
 - iphonesim


You can run "make clean" to remove generated files (for a fresh start)


---------------------------
    PLATFORM SPECIFICS
---------------------------


BlackBerry


You must have the BlackBerry Native SDK installed. Then you should set
BLACKBERRY_NDK_ROOT with the path to the install directory.

In order to configure your environment, you should execute the "bbndk-env"
script which is located with the Native SDK. On Unix platforms you should
call "source bbndk-env.sh" and on Windows you should call "bbndk-env.bat"

Here is an example batch file for building the BlackBerry binaries from
Windows:


set BLACKBERRY_NDK_ROOT=C:\Development\BlackBerry\bbndk-2.0.0
call %BLACKBERRY_NDK_ROOT%\bbndk-env.bat
set OS=blackberry

make clean
make



(Details for other platforms will be added in the future)
