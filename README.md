# Basic-VCPKG-guide

### Note: This guide will only go over using VCPKG with MSBuild (Visual Studio)

## Content Table
1. [Why you want to use VCPKG](#why-you-want-to-use-vcpkg)
2. [Installing VCPKG](#installing-vcpkg)
3. [Basic Commands](#basic-commands)
4. [Extra useful commands](#extra-useful-commands)

---
## Why you want to use VCPKG
There are multiple reasons to use VCPKG over doing it yourself:
- Easy to use with console
- All packages/libraries are stored in the same directory
- The packages will be globaly accessible for MSBuilds
- Works with PreMake5, Cmake and MSBuild 
- You won't have to mess with linker errors anymore
- Cross platform

---
## Installing VCPKG
The installation of VCPKG is quite simple, you can follow the instructions on their [get started page](https://vcpkg.io/en/getting-started.html), but I will sum up the commands I used. I recommend reading this page, since it states certain commands that are not present in the [get started page](https://vcpkg.io/en/getting-started.html).

Installing VCPKG consists of multiple steps and is not as easy as just running an executable.
In the [Basic Commands](#basic-commands) and [Extra useful commands](#extra-useful-commands) section, we will go over some commands that are not mentioned in the [get started page](https://vcpkg.io/en/getting-started.html) but are very usefull. These commands are nearly mandatory to know to use VCPKG properly.

### Prepare a folder
We want to start of by cloning the [VCPKG repo](https://github.com/microsoft/vcpkg) into a local directory. We will need a local directory first, where all the files of VCPKG will be located. I suggest you put this somewhere on your `C:\` drive. 

#### Do not put it into a deep path like `C:\example\trash\directory\path\etc`, since it might cause issues later on (Thank me later).

I personally created an empty directory on my `C:\` drive, called vcpkg. Meaning everything related to VCPKG will be inside of the `C:\vcpkg` directory. I will be using this directory path as an example further in this guide.

### Cloning the repo
So now we clone the [VCPKG repo](https://github.com/microsoft/vcpkg) into that directory we just made.
You can clone the repo in multiple ways:
- Use Git GUI/BASH/CMD and use this command `git clone https://github.com/Microsoft/vcpkg.git` in the `C:\vcpkg` directory.
    #### OR
- Download the latest release of [VCPKG](https://github.com/microsoft/vcpkg/releases) here and extract it in your `C:\vcpkg` directory.
    #### OR
- Feel free to use a different method you are accustomed to.

### Proceeding with the install
Now that you have the repo cloned into your VCPKG directory. We just need to run `bootstrap-vcpkg.bat` to install VCPKG. You can just double click it, no need to use the command line here. 

Once this is done, VCPKG is ready to be used to search, install, update and manage packages for C++ .

---
## Basic Commands
Here I will go over basic commands we can use with VCPKG. These commands are executed within your console, inside of `C:\vcpkg`. 
In this part I will use `SDL2`as an example to install.

### Finding a package
For finding a package we can run: `vcpkg.exe search *package*`

   #### Example: run `vcpkg.exe search SDL2` and you will see all related SDL2 packages that are available.

   #### OR
   
You can also look for packages on the [Browse Packages](https://vcpkg.io/en/packages.html) page. There you can see what command you will have to run to install a specific package.

### Install a package
If we want to install a package we use: `vcpkg.exe install *package*`

   #### Example: run `vcpkg.exe install SDL2` and this will install SDL2
   #### Example: run `vcpkg.exe install SDL2-image`and this will install SDL2-image
         
In [Extra useful commands](#extra-useful-commands) we will see more advanced commands to install different platforms and certain extensions on packages.

### List all installed packages
run `vcpkg.exe list` and it will list all the installed packages

### Update outdated packages
run `vcpkg.exe update` to see all outdated packages
run `vcpkg.exe upgrade` to update the outdated packages

### Integrate into MSBuild
To make sure you can see and access these packages with MSBuild(visual studio), run `vcpkg integrate install`

  #### Beware!, for Cmake this is a different process.

---
## Extra useful commands
### Installing different platforms (x64-windows/linux/...)
We also want to be able to use x64, linux, osx, etc packages. To do this we need to specify it in the command and there are 2 options, use `--triplet=` or `:` suffix.

There are multiple different platforms: arm-uwp, arm64-windows, x64-linux, x64-osx, x64-uwp, x64-windows, x64-windows-static, x86-windows and more. To check what triplets are available, check the [Browse Packages](https://vcpkg.io/en/packages.html). I'm not aware of a command to search for available triplets.

#### Example using `--triplet`->  `vcpkg.exe install SDL2 --triplet=x64-windows`
#### Example using `:`        ->  `vcpkg.exe install SDL2:x64-windows`
This will install the x64-windows version of SDL2.

### Installing bindings
If we are in need of a binding between packages, these bindings are indicated using the `[]`. If there is a binding available, it should show up in the searchlist.
It is just as easy as to run `vcpkg.exe install *package*[*binding*]`. I highly suggest you use the `--recurse` flag when running this command.

#### Example: run `vcpkg.exe install SDL2[vulkan]`, which will install the binding for Vulkan functionality with SDL
