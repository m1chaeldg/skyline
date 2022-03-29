# Building Guide

### Software needed
* [Git](https://git-scm.com/download)
* [Android Studio](https://developer.android.com/studio) - We recommend to get the latest stable version

### Steps
<details><summary><i>Windows only</i></summary>
<p>

> In a terminal prompt with administrator privileges, enable git symlinks globally:
>
> ```cmd
> git config --global core.symlinks true
> ```
> 
> Use this elevated prompt for the next steps

</p>
</details>

Clone the repo **recursively**, either with your preferred Git GUI or with the command below:
```cmd
git clone https://github.com/skyline-emu/skyline.git --recursive
```

Import the skyline folder in Android Studio


## Common issues (and how to fix them)

* `Cmake Error: CMake was unable to find a build program corresponding to "Ninja"`

Check that you installed the correct CMake version in the Android Studio SDK Manager. If you're sure you have the correct one, you may try adding the path to CMake binaries installed by Android Studio to the `local.properties` file:
```properties
cmake.dir=<path-to-cmake-folder>
```
E.g. on Windows:
```properties
cmake.dir=C\:\\Users\\skyline\\AppData\\Local\\Android\\Sdk\\cmake\\3.18.1
```

* `'shader_compiler/*.h' file not found`

You didn't clone the repository with symlinks enabled. Windows requires administrator privileges to create symlinks so it's likely it didn't create them.
In an elevated terminal prompt navigate to the skyline repo folder and run:
```cmd
git submodule deinit app/libraries/shader-compiler
git config core.symlinks true
git submodule foreach git config core.symlinks true
git submodule update --init --recursive app/libraries/shader-compiler
```
If you'd like to, you can enable symlinks globally by running
```cmd
git config --global core.symlinks true
```
This will only affect new repositories
