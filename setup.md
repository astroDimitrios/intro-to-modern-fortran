---
title: Setup
---

## Data Sets

Download the [zip file](https://github.com/astroDimitrios/intro-to-modern-fortran)
and unzip it in your Desktop **or** check out this lessons
[git repository](https://github.com/carpentries-incubator/intro-to-modern-fortran/) and navigate to the following directory:
`episodes/data/learners`.
This contains data and skeleton code which we will use throughout the course.
This course refers to this `learners` directory
as the **data directory** from this point on.

## Compiler Setup

Fortran is a compiled language.
You have to translate your Fortran code to machine code
before running the program.
We can do this with a Fortran compiler.
It is common to test your code with multiple compilers,
as some are better at debugging certain errors than others.

### Installing a Compiler

Your instructor may provide different instructions for installing
a suitable compiler or have installed one for you.
If you need to install a compiler yourself follow the instructions below.
We recommend installing **GFortran**[1] as your first compiler.

::: group-tab

### GFortran

GFortran is a free open source compiler.
It is part of the Gnu Compiler Collection (GCC).
Comprehensive installation instructions are on the
[GFortran install page on fortran-lang][install-gfortran].

You can also install GFortran via conda:

```bash
$ conda install gfortran 
```

### Intel

The Intel Fortran compiler is free through their oneAPI toolkit.
[Linux Install Instructions](https://www.intel.com/content/www/us/en/docs/oneapi/installation-guide-linux/2025-0/intel-fortran-essentials.html#GUID-E8EA92E5-84BC-4550-9988-4A9147A1B769)
[Windows Install Instructions](https://www.intel.com/content/www/us/en/docs/oneapi/installation-guide-windows/2025-0/intel-fortran-essentials.html)
The Intel compiler is not available for MacOS.

You can also install the Intel compiler via conda:

```bash
$ conda install intel-fortran-rt
```

### Flang

LLVM Flang is another open source compiler
based on the LLVM compiler toolkit.
Flang is installed from the LLVM source code.
If you have not built programs from source before
we recommended choosing another compiler
or installing Flang via conda.
[Link to the Flang Getting Started page](https://flang.llvm.org/docs/GettingStarted.html)

You can also install the Flang compiler via conda:

```bash
$ conda install flang
```

### Cray

The [HPE Cray Fortran compiler](https://cpe.ext.hpe.com/docs/latest/cce/index.html)
is proprietary but highly optimised.
Your organisation may have a license for the Cray compiler.

:::

### Testing your compiler

Now you have a compiler installed you can compile a simple program.
In the [data directory](./setup.md#data-sets)
navigate to `setup/hello_world.f90`.
This is a Fortran program which contains:

```fortran
program hello_world

    implicit none

    print *, 'Hello World!'

end program

```

Open a terminal.
Enter the setup directory:

```bash
$ cd <path-to-your-data-directory>/setup
```

To compile the program run:

::: group-tab

### GFortran

```bash
$ gfortran hello_world.f90
```

### Intel

```bash
$ ifx hello_world.f90
```

### Flang

```bash
$ flang hello_world.f90
```

### Cray

```bash
$ ftn hello_world.f90
```

:::

You should see a new file in the directory:

```bash
$ ls
```

```output
a.out hello_world.f90
```

The `a.out` file is your compiled program.
To run the program:

```bash
$ ./a.out
```

```output
Hello World!
```

You have compiled your first Fortran program!
The first episode in this lesson will
cover compiling in more detail.

## Text Editors and Integrated Development Environments (IDEs)

While Fortran files are plain text and can be edited with any plain text editor, it is recommened that you use an editor that is capable of _syntax highlighting_. Setup instructions for some editors are available below.

### Emacs

[Emacs][emacs-link] is a cross-platform text editor available for Linux, MacOS, and Windows. Emacs applies syntax highlighting for most Fortran files, but additional file extensions, such as `.X90`  may be valid Fortran files but will not be picked up in Emacs _f90-mode_. This mode allows for tab-completion of Fortran statements and the addition of a drop-down menu that provides additional Fortran-related options.

Files can be manually set to f90-mode using `M-x f90-mode`, but file extensions can be added to your [Emacs initialization file][emacs-init-link] to ensure that these are recognised when opened. The format for this is
```lisp
(setq auto-mode-alist
      (append '(("\\.mf90" . f90-mode)
                ("\\.X90" . f90-mode)
        ) auto-mode-alist))
```
::::::::::::::::: tab

### Windows/MacOS

From your home directory, initialization settings can be placed within your `.emacs.d/init.el` file.

### Linux

Initialization settings can be placed within your `~/.config/emacs/init.el` file. This location follows the Linux desktop environment guidelines.

### Legacy (cross platform)

The `.emacs` or `.emacs.el` file is an older method of configuring Emacs. This file is held in your home directory.

:::::::::::::::::::::::::
