Bootstrap C and C++ Projects
============================
Quickly spin up a minimal C or C++ project under Linux.

Save as files in your `$PATH`.

C Project
---------
```bash

#!/bin/bash
# Spin up a minimal C project
# ===========================================================================================================
function generate_makefile {
	mkdir bin
	cat << 'EOF' > Makefile
SOURCES:= $(wildcard *.c) $(wildcard *.h)
OBJECTS:= $(wildcard *.c)
OUT:= bin/main
main: $(SOURCES)
	cc -W -Wall -fsanitize=address -g -o $(OUT) $(OBJECTS)
EOF
}

function generate_main {
	cat << 'EOF' > main.c
#include <stdio.h>

int main()
{
	// Code
	return 0;
}
EOF
}

generate_makefile
generate_main
```

C++ Project
-----------

```bash

#!/bin/bash
# ===========================================================================================================
function generate_makefile {
  mkdir bin
  cat << 'EOF' > Makefile
SOURCES:= $(wildcard *.cpp) $(wildcard *.hpp)
OBJECTS:= $(wildcard *.cpp)
OUT:= bin/main
main: $(SOURCES)
	g++ -W -Wall -std=c++17 -g -o $(OUT) $(OBJECTS)

debug: $(SOURCES)
	g++ -W -Wall -std=c++17 -g -o $(OUT) $(OBJECTS)
EOF
}

function generate_main {
  cat << 'EOF' > main.cpp
#include <iostream>

int main()
{
	std::cout << "+++Out of Cheese Error+++\n+++Redo From Start+++" << std::endl;
	return 0;
}
EOF
}

generate_makefile
generate_main
```

