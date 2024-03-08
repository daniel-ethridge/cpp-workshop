# C++ Resources (How did I learn?)
I learned all this very slowly over time. Often times it was a frustrating experience, so my goal is to:
- Catalyze the starting experience for you all
- Explain some seemingly simple things that took a while for me to understand
- Provide all the resources that I've used over time to learn.
- Show you some cool libraries to use for different things.

# How did I learn?
- Youtube Channels
    - The Cherno (specifically https://www.youtube.com/playlist?list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb)
    - Derek Banas (https://www.youtube.com/playlist?list=PLGLfVvz_LVvQ9S8YSV0iDsuEU8v11yP9M). <i>Note that Derek also teaches a lot of other things that he somehow learned. Examples include React (frontend framework), Blender (3D modeling), Qt (C++ framework with GUI capabilities), statistics, and trigonometry.</i>
    - (For QT and QML): https://www.youtube.com/playlist?list=PL6CJYn40gN6hdNC1IGQZfVI707dh9DPRc 
- Stackoverflow (Hit or miss here. There is a bit of an art to knowing what is actually helpful.)
- Documentation
    - https://en.cppreference.com/w/
    - https://cplusplus.com/
- Asking for help!

# Preprocessing, Compilation, and Linking
I know what these steps are but can never remember the best way to describe them, so this is largely taken from https://stackoverflow.com/questions/6264249/how-does-the-compilation-linking-process-work.
## Preprocessing
The preprocessor handles the preprocessor directives, like `#include` and `#define`. Expands different macros and includes files. Output sent to compiler.

## Compilation
The compilation step is performed on each output of the preprocessor. The compiler parses the pure C++ source code (now without any preprocessor directives) and converts it into assembly code. Then invokes underlying back-end(assembler in toolchain) that assembles that code into machine code producing actual binary file in some format(ELF, COFF, a.out, ...). This object file contains the compiled code (in binary form) of the symbols defined in the input. Symbols in object files are referred to by name.

Object files can refer to symbols that are not defined. This is the case when you use a declaration, and don't provide a definition for it. The compiler doesn't mind this, and will happily produce the object file as long as the source code is well-formed.

## Linking
The linker is what produces the final compilation output from the object files the compiler produced. This output can be either a shared (or dynamic) library (and while the name is similar, they haven't got much in common with static libraries mentioned earlier) or an executable.

It links all the object files by replacing the references to undefined symbols with the correct addresses. Each of these symbols can be defined in other object files or in libraries. If they are defined in libraries other than the standard library, you need to tell the linker about them.

At this stage the most common errors are missing definitions or duplicate definitions. The former means that either the definitions don't exist (i.e. they are not written), or that the object files or libraries where they reside were not given to the linker. The latter is obvious: the same symbol was defined in two different object files or libraries.

# Dynamic (Shared) Libraries vs Static Libraries
## Dynamic (Shared)
Separate library file that must be shipped with executable. Slower, but offers smaller executable file

## Static
Library functionality is built into the executable itself. Faster, but larger executable

# Directory Structure
I like to use:
```
├── build
├── CMakeLists.txt
├── include
├── README.md
├── src
└── test
```

# CMake
Open the `CMakeLists.txt` file. Let's get a simple project going. 

## Generating Build Files and Building
### Method A
- `cd <PROJ_DIR>/build`
- `cmake .. `
- `cmake --build .`

### Method B
- `cd <PROJ_DIR>`
- `cmake -B build -S .`
- `cmake --build build`

## Installing (Just to note; we don't need to do this right now)
- `cd <PROJ_DIR>/build`
- `cmake install .`

# Adding Other Headers and Sources
Let's put some files in include and src. What functionality do we want?
