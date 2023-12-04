# SPAdd

SPAdd is a VST-software synthesizer for spatial additive synthesis.

## Overview
Spatial additive synthesis can be efficiently implemented by applying the inverse Fourier transform to create the individual channels of Ambisonics signals. This approach has been implemented as an audio plugin, allowing the generation of dynamic spatial waveforms in a typical music production context.

## Prerequisites
* CMake 3.10 or newer for building
* C++17 compatible standard C++ library
* Clang 9+
* Ninja (recommended for faster builds and mandatory for the default CMake Presets)

## Building
Clang is required at this moment due to KFR.

CMake Presets provide an easy way to build the targets.

For example on Windows run a x64 Native Tools Command Prompt or set the default parameters manually according to your VSCode version:
```
"C:\\Program Files\\Microsoft Visual Studio\\2022\\Community\\VC\\Auxiliary\\Build\\vcvars64.bat"
```

For all platforms run
```
cmake --preset x64-Debug-Clang
```
and
```
cmake --build --preset x64-Debug-Clang-Build
```

Otherwise have a look a the platform specific instructions below.

### Linux
Use the CMake build and compile commands. Make sure to install clang using your package manager and add the following defines to the cmake command line:
```
cmake -DCMAKE_CXX_COMPILER=clang++ -DCMAKE_C_COMPILER=clang ...
```

### Windows
Generate a project for Visual Studio:
```
cmake -G "Visual Studio 1X 20XX" -T ClangCL -A x64 -S/path/to/project/SPAdd -B/path/to/project/SPAdd/build
```
### macOS
Generate a project for Xcode:
```
cmake -G Xcode -B build
```
## Benchmarking
For benchmarking the constants in PluginProcessor.h can be adjusted and the timer constructor has to be placed inside a scope together with the part of the code intended to be measured.

## Related Repositories
This repository is based on Eyal Amir's "JUCE CMake Repo Prototype"
https://github.com/eyalamirmusic/JUCECmakeRepoPrototype

Optional package management CPM.cmake:
https://github.com/TheLartians/CPM.cmake
It automatically fetches JUCE from git, but you can also set the variable:
CPM_JUCE_SOURCE to point it to a local folder, by using:
``-DCPM_JUCE_SOURCE="Path_To_JUCE"``
when invoking CMake

JUCE can be found here:
https://github.com/juce-framework/JUCE

KFR can be found here:
https://github.com/kfrlib/kfr
