# RGF Version 1.3

### C++ Programs for Regularized Greedy Forest (RGF)

************************************************************************

# 0.0 Changes

Please see the file [`CHANGES.md`](./CHANGES.md) for the changelog of RGF.

# 0.1 Acknowledgements

  We thank **Dave Slate** for suggesting a solution to the issue of file size
  restriction.

************************************************************************

# Contents:

1. [Introduction](#1-introduction)

   1.1. [System Requirements](#11-system-requirements)

2. [Download and Installation](#2-download-and-installation)

3. [Creating the Executable](#3-creating-the-executable)

   3.1. [Windows](#31-windows)

   3.2. [Unix-like Systems](#32-unix-like-systems)

   3.3. [[Optional] Endianness Consideration](#33-optional-endianness-consideration)

4. [Documentation](#4-documentation)

5. [Contact](#5-contact)

6. [Copyright](#6-copyright)

7. [References](#7-references)

# 1. Introduction

This software package provides implementation of regularized greedy forest
(RGF) described in [[1]](#7-references).

## 1.1. System Requirements

Executables are provided only for some versions of Windows
(see [Section 3](#3-creating-the-executable)) for detail).
If provided executables do not work for your environment,
you need to compile C++ code.

To use the provided tools and to go through the examples
in the [user guide](./rgf-guide.rst#2-get-started-a-quick-tour-of-functionality), Perl is required.

# 2. Download and Installation

[Download](https://github.com/RGF-team/rgf/archive/master.zip) the package and extract the content.
Otherwise, you can use git

```
git clone https://github.com/RGF-team/rgf.git
```

The top directory of the extracted (or cloned) content is `rgf`
and this software package is located into `RGF` subfolder.
Below all the path expressions are relative to `rgf/RGF`.

# 3. Creating the Executable

To go through the examples in the [user guide](./rgf-guide.rst), your executable needs to be
at the `bin` directory (it will appear there after you compile it by any method from the listed below).
Otherwise, your executable can be anywhere you like.

## 3.1. Windows

### 3.1.1. Precompiled File

The easiest way. Just download the precompiled file `rgf.exe`
from the latest [GitHub release](https://github.com/RGF-team/rgf/releases).

### 3.1.2. Visual Studio (Using the Provided Solution File)

1. Open directory `Windows/rgf`.
2. Open `rgf.sln` file with Visual Studio.

   If you are asked to upgrade the solution file, click `OK`.

3. Choose `Release` from the **Solution Configurations** listbox
   and `Win32` or `x64` depending on your machine architecture from the **Solution Platforms** listbox on the standard toolbar.
4. Choose `BUILD -> Build Solution (Ctrl+Shift+B)`.

   If you have errors about **Platform Toolset**, go to `PROJECT -> Properties -> Configuration Properties -> General`
   and select the toolset installed on your machine.

### 3.1.3. MinGW (Using the Provided makefile)

Build executable file with MinGW g++ from existing `makefile`
(you may want to customize this file for your environment).

```
mkdir bin
cd build
mingw32-make
```

### 3.1.4. CMake and Visual Studio

Create solution file with CMake and then compile with Visual Studio.

```
cd build
cmake ../ -G "Visual Studio 10 2010"
cmake --build . --config Release
```

If you are compiling on 64-bit machine, then add `-A x64` to the end of command: `cmake ../ -G "Visual Studio 10 2010" -A x64`.

We tested following versions of Visual Studio:

- Visual Studio 10 2010 [Win64]
- Visual Studio 11 2012 [Win64]
- Visual Studio 12 2013 [Win64]
- Visual Studio 14 2015 [Win64]
- Visual Studio 15 2017 [Win64]
- Visual Studio 16 2019 [Win64]

Other versions may work but are untested.

### 3.1.5. CMake and MinGW

Create `makefile` with CMake and then compile with MinGW.

```
cd build
cmake ../ -G "MinGW Makefiles"
cmake --build . --config Release
```

## 3.2. Unix-like Systems

### 3.2.1. g++ (Using the Provided makefile)

Build executable file with g++ from existing `makefile`
(you may want to customize this file for your environment).

```
mkdir bin
cd build
make
```

### 3.2.2. CMake

Create `makefile` with CMake and then compile.

```
cd build
cmake ../
cmake --build . --config Release
```

## 3.3. [Optional] Endianness Consideration

The models obtained by RGF training can be saved to files.
The model files are essentially snapshots of memory that include
numerical values. Therefore, the model files are sensitive to
"endianness" of the environments. For this reason, if you wish to
share model files among environments of different endianness, you need
to follow the instructions below. Otherwise, you can skip this section.

To share model files among the environments of different endianness,
build your executable for the environment with big-endian with the
compile option:

```
/D_AZ_BIG_ENDIAN_
```

By doing so, the executable in your big-endian environment swaps the
byte order of numerical values before writing and after reading the
model files.

# 4. Documentation

Please see the file [`rgf-guide.rst`](./rgf-guide.rst) "**Regularized Greedy Forest: User Guide**".

# 5. Contact

Please post an [issue](https://github.com/RGF-team/rgf/issues)
at GitHub repository for any errors you encounter.

# 6. Copyright

RGF is distributed under the **MIT license**.
Please read the file [`COPYING`](./COPYING).

# 7. References

[1] Rie Johnson and Tong Zhang. [Learning Nonlinear Functions Using
    Regularized Greedy Forest.](https://arxiv.org/abs/1109.0887)
    IEEE Transactions on Pattern Analysis and Machine
    Intelligence, 36(5):942-954, May 2014.
