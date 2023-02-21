# Project DG - General Purpose Game and Application Engine

**Project DG** is a two-dimensional general-purpose game and application engine, with three-dimensional features possibly planned for the future. It is written in C++, using the C++20 language specification, and will follow along loosely with [The Cherno's](https://www.youtube.com/@TheCherno) [Game Engine Development Series](https://www.youtube.com/playlist?list=PLlrATfBNZ98dC-V-N3m0Go4deliWHPFwT).

## Table of Contents

- Build Tools
- Dependencies
- Folder Structure
- Naming Convention and Guidelines
  - Source Files and Folders
  - Source Code
  - Coding Guidelines

## Build Tools

To build the DG Engine library and its client applications, you will need the following tools:

- **[Conan](https://conan.io)** - An open-source, decentralized package manager for C and C++ application dependencies.
- **[Premake](https://premake.github.io)** - A build configuration system which uses Lua scripts to generate build files.

## Dependencies

The DG Engine and its client applications will require the following dependencies:

- **[GLFW](https://www.glfw.org)** - An open-source library which provides windowing; input and events; and context creation for OpenGL applications.
- **[GLEW](https://glew.sourceforge.net)** - An open-source extension-loading library for OpenGL applications.

## Folder Structure

The project's folders will be structured as follows:

- `assets` - Contains any external assets which will be used by the client applications. The DG Engine library's code itself shall **NOT** require the use of external assets.
- `build` - Contains the output of source compilation and linking.
  - `bin` - Contains the compiled binaries. The engine library and client application executables should be located here.
  - `obj` - Contains the compiled object files which will be linked into the resulting engine library and client applications.
- `externals` - Contains the source code of the project's external dependencies.
- `generated` - Contains the build files generated by Conan and Premake.
- `projects` - Contains the engine library's and client applications' source code.
  - Each project shall be contained within its own subfolder.
  - Each project subfolder shall contain the following folders:
    - `include` - Contains the project's header files and inline header files.
    - `src` - Contains the project's source files.
- `scripts` - Contains useful script files (bash scripts, batch files, etc.), generally for the purpose of generating build files and compiling sources.

## Naming Convention and Guidelines

### Source Files and Folders

The source code files, and their containing folders within the `project` subfolders' `include` and `src` folders shall use the following naming convention:

- Project Folders and Filenames: `PascalCase`
- Header File Extension: `.hpp`
- Inline Header File Extension: `.inl`
- Source File Extension: `.cpp`

Asset files within the `assets` folder need not necessarily abide by the above naming conventions, but it is recommended.

### Source Code

The source code itself shall abide by the following naming convention:

- Functions: `camelCase`
- Function parameters: `camelCase`
- Variables: `camelCase`
- Global Constants: `SCREAMING_SNAKE_CASE`
- Local Constants: `PascalCase`
- Class, Struct and Enum Names: `PascalCase`
- Class Member Functions: `camelCase`
- Class Member Variables: `m_camelCase`
- Class Static Member Variables: `s_camelCase`
- Class Static Member Constants: `PascalCase`
- Struct Member Variables: `camelCase`
- Enum Constants: `PascalCase`
- Macros: `DG_SCREAMING_SNAKE_CASE`
- Macro Arguments: `camelCase`

### Coding Guidelines

- All engine library code shall live inside the following namespace:

```c++
namespace dg {

}
```

- As much as possible, document each function, class, constant, etc. with the following syntax:

```c++
/**
 * @brief Describes the purpose of a constant or member variable, and what a
 * function does.
 * @param[in]  variableNameOne      Describes an input variable name.
 * @param[out] variableNameTwo      Describes an output variable name.
 * @return Describes a function's return value.
 * @note Provides additional details about this constant, member variable
 * or function.
 * @warning Provides important warnings that a developer should take heed
 * of when using this function, constant or member variable.
 */
```

- Try to keep your lines of code and comments within 80 characters per line, or as close to 80 characters if need be.
- Inform your compiler to watch for all warnings and extra warnings, and to treat warnings as errors. This will reduce the likelihood of bugs occuring in your code.
  - In GNU G++, you can use the following command-line arguments: `-Wall -Wextra -Werror`.
