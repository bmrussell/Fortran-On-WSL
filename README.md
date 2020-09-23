# FORTRAN Debugging on WSL from Windows

## **Intro**
Watch the [Visual Studio Code videos](https://code.visualstudio.com/docs/getstarted/introvideos) for a tour of the features. This will help a lot.


## **Vscode Setup (Windows)**
---
1. Install the following extensions:
- **C/C++** (Microsoft)
- **fortran** (Xavier Hahn) 
- **Fortran Breakpoint Support** (ekibun)

2. gfortran Setup (wsl Linux)

    ```
    sudo apt install gfortran build-essential gdb
    ```

3. Open vscode from Linux

- Open  WSL terminal and cd into the folder
    ```
    cd code/fortran/hello-world/
    ```

- open vscode from linux and open the current directory
    ```
    code .
    ```

- Create a fortran file `hello-world.f90` containing
    ```fortran
    program hello
        print *, "Hello There"
        print *, "General Kenobi"
    end program
    ```

- Click the Launch & Debug menu icon and "create a launch.json file"

- Select "Fortran (GDB)"

- Change the configuration for "program" as follows and save:
    ```
    "program": "${workspaceFolder}/a.out",
    ```

3. Compile 

- Open a terminal in vscode (Terminal->New Teminal or Ctrl+Shift+')
- Enter the following command

    ```
    gfortran hello-world.f90 -g -Wall -Wextra -Warray-temporaries -Wconversion -fimplicit-none -fbacktrace -ffree-line-length-0 -fcheck=all -ffpe-trap=zero,overflow,underflow -finit-real=nan
    ```
    [Source](http://fortranwiki.org/fortran/show/Debugging+tools)

    This generates an executable called `a.out` by default, hence the setting in the launch.json

4. Hit f5 with hello-world.f90 open to debug!

