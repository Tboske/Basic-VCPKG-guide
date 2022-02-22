# Basic-VCPKG-guide

### Note: This guide will only go over using VCPKG with MSBuild (Visual Studio)

## Content Table
1. [Why you want to use VCPKG](#why-you-want-to-use-vcpkg)
2. [Installing VCPKG](#installing-vcpkg)
3. [Basic Commands](#basic-commands)
4. [Extra useful commands](#extra-useful-commands)

---
## Why you want to use VCPKG
I think there are multiple reasons to use VCPKG over doing it yourself:
- All packages/libraries are stored in the same directory
- Easy to manage with console
- The packages will be globaly accessible for MSBuilds
- Works with PreMake5, Cmake and MSBuild 
- You won't have to mess with linker errors anymore

---
## Installing VCPKG
The installation of VCPKG is quiete simple, you can follow the instructions on their [get started page](https://vcpkg.io/en/getting-started.html). But I'll sum up the commands I used. Installing VCPKG consists out of multiple steps and is not as easy as just running a executable.

### Prepare a folder
We want to start of by cloning the [VCPKG repo](https://github.com/microsoft/vcpkg) into a local directory. But we need a local directory first where everything will be located. I would suggest you put this in your `C:\` drive. Also don't put it into a deep path like `C:\example\trash\directory\path\etc`, since it might cause issues (Thank me later).
I personally went with `C:\vcpkg` and I will use this as example going onwards in this guide.


### Cloning the repo
So now we clone the [VCPKG repo](https://github.com/microsoft/vcpkg) into that directory we just made.
You can clone the repo in multiple ways:
- Use Git GUI/BASH/CMD and use this command `git clone https://github.com/Microsoft/vcpkg.git` in the directory `C:\vcpkg`.
    #### OR
- Download the latest release of [VCPKG](https://github.com/microsoft/vcpkg/releases) and extract it in your folder `C:\vcpkg`.
- Feel free to use another way you are already accustomed to.

### Proceeding with the install
Now that you have the repo cloned into your VCPKG directory. We just need to run `.\vcpkg\bootstrap-vcpkg.bat` to install VCPKG. 

Once done, we are ready to use VCPKG to search, install and manage packages for C++.

---
## Basic Commands

---
## Extra useful commands

