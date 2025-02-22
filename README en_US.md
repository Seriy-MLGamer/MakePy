<!--
MIT Expat license

(C) 2025 Серый MLGamer <Seriy-MLGamer@yandex.ru>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
-->

# MakePy

Advanced build from source code as easy as in package manager.

	python make.py build revolution

*The Revolution in source code management!* **MakePy** is a *free* framework for Python language which you can use to do a variety of operations on your source code and other files on different operating systems and processor architectures. An excellent alternative to Make, CMake and similar programs.

## Advantages

### The Power of Python!

A build script is programmed in **Python** language which is a Turing-complete general-purpose programming language allowing procedural, functional, object-oriented and other styles of programming. *No more tasks hard or impossible to solve in proprietary programming languages of well-known build programs.*

### Full build cycle

**Just one command** initiates a full build cycle: from source code compilation to packages packing. *A high level of automation is achieved.*

### Convenient interface

Command line interface can be **comfortable** too. *User experience of this build system reminds of package manager.* Build targets are divided into paths (files and folders) and packages. First you enter an action being performed on paths and packages, then you enumerate paths and packages.

	./make.py [action] {<path or package>|path:<path>|package:<package>} [...]

### The system you can adjust on your own

The framework is **object-oriented**. *Based on the available classes, you can make yours with very different contents and behavior.* You can use both the built-in toolkit and the one you added yourself. You can add your actions and your types of targets.

## Built-in features

  * Creation of folders
  * Automatic addition of targets for creation of folders
  * Creation of symbolic links
  * Compilation of object files
  * Linking of executable files
  * Linking of static libraries
  * Linking of shared libraries
  * Generation of static interfaces for ".dll" shared libraries
  * Extraction of symbols lists (".def" files) from ".dll" shared libraries
  * Cleanup of working folder from generated files and folders with automatic detection of files and folders being deleted
  * Installation of files and folders with pre-installation of packages-dependencies
  * Removal of installed files and folders with automatic detection of files, folders and dependent packages being deleted
  * Packing of generated files and folders into an archive or package

Currently built-in framework features support C and C++ programming languages, GCC and Clang compilers and GNU/Linux and Windows operating systems. You can pack a Debian (".deb") package on Debian-based GNU/Linux distribution using tools from package `debhelper` (you also need to use "sample debian rules" file located in repository as "debian/rules" file).

## Usage

Add "makepy.py" file from the repository to your project folder or to a Python modules folder.

Create a build script in the project folder and name it, for example, "make.py".

### Build script example

	#!/usr/bin/python3 -B
	
	from makepy import *
	
	class Hello_Revolution(MakePy):
		def main(self, defines):
			Package(self, "build", "revolution", {"build": Dependencies([self.executable("revolution")])})
			Executable_C(self, "revolution", "main.o")
			Object_C(self, "main.c")
			Clean(self, "revolution")
	Hello_Revolution("revolution", "build", "package").make()

Run the build script.

### Bash

	$ ./make.py

### CMD

	>python make.py

### Project tree before launch

	src
	  main.c
	make.py
	makepy.py

### Project tree after launch

	bin
	  revolution{.exe}
	obj
	  main.o
	src
	  main.c
	make.py
	makepy.py

To learn more about the framework, enter these commands:

### Python console

	>>> import makepy
	>>> help(makepy)

And also this command:

### Bash

	$ ./make.py --help

### CMD

	>python make.py --help

*Out-of-source program build must be simple for user.*

Do you think so? Use **MakePy**!

# Further development

Definitely, this is not the end. There is a list of things demand addition.

  1. More detailed documentation
  2. Stability and safety of use improvements
  3. Build script code perception improvements
  4. Multithreading
  5. Progress bar
  6. Support for other compilers
  7. Support for other programming languages
  8. Support for other operating systems
  9. Packing of other types of packages
  10. Source code analysis (automatic dependencies detection)
  11. Backward compatibility
  12. Addition to the PyPI repository
  13. Isn't it enough what else