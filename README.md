# C-Playground

A small playground for C and C++ projects using CMake. 

## Quick Start

### Create a new app from the template:

Copy the template folder and give it a new name (example: `MyApp`):

```bash
cp -R template MyApp
```

### (Optional) Update the project name:

Open `MyApp/CMakeLists.txt` and change the `project(...)` name if you want
the executable to have a matching name. The template uses `TemplateApp` by
default.

```cmake
cmake_minimum_required(VERSION 3.22)

project(TemplateApp # Project Name
    VERSION
        0.0.1
    LANGUAGES
        C
        CXX
)
```

### Build:

```bash
cd MyApp
cmake -S . -B build
cmake --build build
```

### Run the built binary:

```bash
./build/MyApp
```

## Template Layout

- `template/` — the template root directory
	- `CMakeLists.txt` — application CMake file
	- `include/` — headers (e.g. `hello.h`)
	- `src/` — source files (e.g. `main.c`, `hello.c`)

## Quick Verification Example:

```bash
# create and build a test app
cp -R template MyTestApp
cd MyTestApp
cmake -S . -B build
cmake --build build
./build/TemplateApp
```

## Building Multiple Apps (MegaBuild)

The root level `CMakeLists.txt` can be configured to build all applications by
doing a CMake build in the root rather than the subfolders. To add applications
to the MegaBuild, simply add an `add_subdirectory()` call in the root level
CMake file

```cmake
cmake_minimum_required(VERSION 3.22)

project(CmakeProjectTemplate
    VERSION
        0.0.1
    LANGUAGES
        C
        CXX
)

add_subdirectory(template)
add_subdirectory(NewApp) # Your application 
```

Running the MegaBuild is the same as the individual subfolder builds.

```bash
# In the project root
cmake -S . -B build
cmake --build build
```

Compiled binaries will be found in the subdirectory given to the
`add_subdirectory()` call. In the example above, the `NewApp` binary would be
executed as the following:

```bash
# In the project root
./build/NewApp/NewApp
```