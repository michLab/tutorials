# Notes on qmake build process

Based on [docs](https://doc.qt.io/qt-5/qmake-manual.html)

## General variables

|Variable|Contents|
|-|-|
|CONFIG|	General project configuration options.|
|DESTDIR|	The directory in which the executable or binary file will be placed.|
|FORMS|	A list of UI files to be processed by the user interface compiler (uic).|
|HEADERS|	A list of filenames of header (.h) files used when building the project.|
|QT|	A list of Qt modules used in the project.|
|RESOURCES|	A list of resource (.qrc) files to be included in the final project. See the The Qt Resource System for more information about these files.|
|SOURCES|	A list of source code files to be used when building the project.|
|TEMPLATE|	The template to use for the project. This determines whether the output of the build process will be an application, a library, or a plugin.|

### CONFIG
Based on [docs](https://doc.qt.io/qt-5/qmake-variable-reference.html#config)
Specifies project configuration and compiler options. The values are recognized internally by qmake and have special meaning.

```code
CONFIG += c++14
```

### DEFINES

Like C preprocessor macros (-D option), e.g.:
```code
DEFINES += DEBUG
```
### DEPENDPATH
Specifies a list of directories for qmake to scan, to resolve dependencies. This variable is used when qmake crawls through the header files that you #include in your source code.

### INCLUDEPATH
Specifies the #include directories which should be searched when compiling the project.

### DEPENDPATH vs INCLUDEPATH

Based on [topic](https://www.qtcentre.org/threads/17346-QMake-s-INCLUDEPATH-and-DEPENDPATH-problems#:~:text=INCLUDEPATH%20is%20used%20during%20compilation,when%20certain%20header%20file%20changes.)

INCLUDEPATH is used during compilation to find included header files. DEPENDPATH is used to resolve dependencies between header and source files, eg. which source files need to be recompiled when certain header file changes. If you modify a header file in folder foo/ and foo/ is not listed in DEPENDPATH, nothing gets recompiled. If foo/ is listed in DEPENDPATH, source files depending on that header will get recompiled. Paths can be relative to the .pro file or absolute paths.

### LIBS
Specifies a list of libraries to be linked into the project. If you use the Unix -l (library) and -L (library path) flags, qmake handles the libraries correctly on Windows (that is, passes the full path of the library to the linker). The library must exist for qmake to find the directory where a -l lib is located.

For example:
```code
unix:LIBS += -L/usr/local/lib -lmath
win32:LIBS += c:/mylibs/math.lib
```

### TEMPLATE

Specifies the name of the template to use when generating the project. Some ot the allowed values are:

|Option|	Description|
|-|-|
|app|	Creates a Makefile for building applications (the default). See Building an Application for more information.|
|lib|	Creates a Makefile for building libraries. See Building a Library for more information.|
|subdirs|	Creates a Makefile for building targets in subdirectories. The subdirectories are specified using the SUBDIRS variable.|

## VERSION
```code
VERSION: A.B.C
```

## User Variables

VAR = foobar => Assign value to variable when qmake is run
$$VAR => QMake variable's value at the time qmake is run
$${VAR} => QMake variable's value at the time qmake is run (identical but enclosed to separate from surrounding text)
$(VAR) => Contents of an Environment variable at the time Makefile (not qmake) is run
$$(VAR) =>Contents of an Environment variable at the time qmake (not Makefile) is run


## Building a library
```code
TEMPLATE = lib
TARGET = fooname
unix:DESTDIR = $$VAR/lib
HEADERS += foo.h \
    bar.h
SOURCES += foo.cpp \
    bar.cpp
unix:LIBS += lfoo
```

## .pro vs .pri files

Based on Stackoverflow [topic](https://stackoverflow.com/questions/8358627/qt-pro-vs-pri)

.pro
This is usually called Project File.

.pri
This is usually called Project Include File.

As you can see in their names, the main difference is that .pri files are meant to be include files. That is similar to including modules in programming language to share the functionality, essentially.

You will be able to write the common settings and code into those .pri files and include them from several .pro files as the need arises. 


