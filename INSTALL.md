# EGSnrc installation instructions

As a general-purpose Monte Carlo software toolkit, EGSnrc is not a stand-alone software which you simply download and run. Rather, it provides source code and utilities to help you write, compile and run your own radiation transport simulations. Some standard applications are provided as part of EGSnrc (e.g., the dosxyznrc application to calculate radiation dose in a rectilinear voxel grid) but you still have to compile such applications from source code using common software development tools, which must be installed on your system *before* you install EGSnrc.

Installation involve three steps: 1) install prerequisite software; 2) download EGSnrc to your computer; and 3) configure EGSnrc for use on your system (and optionally compile standard applications distributed as part of EGSnrc). Instructions for each of these steps are provided below, for [Linux](#installing-egsnrc-on-linux), [OSX](#installing-egsnrc-on-osx) and [Windows](#installing-egsnrc-on-windows) systems. The preferred platform is Linux, on which EGSnrc is developed. 


## Installing EGSnrc on Linux

### 1. Install prerequisite software

Before installing EGSnrc on Linux please ensure the following software is installed. These are very common and widely available software packages, often installed by default on many Linux distributions. Otherwise you can easily find and install them through your package manager, or else ask your system administrator to install them:

1. a Fortran compiler (preferably `gfortran`)
2. a C compiler (preferably `gcc`)
3. a C++ compiler (preferably `g++`)
4. the GNU `make` utility
5. the Tcl/Tk interpreter and widget toolkit, version 8.0 or later
6. the Grace plotting tool (providing the `xmgrace` command)


#### Compilers

You may use any working Fortran, C and C++ compilers on your system. We develop and use EGSnrc with the GNU compilers `gfortran`, `gcc` and `g++`, so these are recommended. If you use other compilers, you may have to adjust compilation options in the configuration stage in order for EGSnrc to work as expected with your compilers. To check that you have working Fortran, C and C++ compilers, open a terminal shell and issue the following commands (or equivalent ones if you are using other compilers):
```bash
gfortran --version                                  # should report your Fortran compiler version
gcc --version                                       # should report your C compiler version
g++ --version                                       # should report your C++ compiler version
```

#### GNU make

EGSnrc relies on a `make` tool, which controls and automates the software building process: most EGSnrc applications are built by issuing the `make` command in the appropriate directory. There are various implementations of `make`, but EGSnrc relies on features of the GNU implementation (also called `gmake` on some systems). To check that `make` invokes GNU make on your system, open a terminal shell and issue the following command:

```bash
make --version                                      # should report "GNU Make" on first line
```

#### Tcl/Tk and Grace

While Tcl/Tk and Grace are not essential to run EGSnrc simulations, they prove useful if you want to use EGSnrc graphical user interfaces and display data plots generated by EGSnrc applications. Note that Tcl/Tk is normally installed by default in most Linux distributions. If you want to check that Tcl/Tk and Grace are available on your system, open a terminal shell and issue the following commands:

```bash
echo 'puts [info patchlevel]; exit 0' | wish        # (optional) should report version 8.0 or newer
grace -version                                      # (optional) should report Grace-5.0 or newer
```


### 2. Download EGSnrc

To use the EGSnrc toolkit you must copy the entire EGSnrc directory tree to your computer. All the project files are grouped in a single top-level `EGSnrc` directory which you can put just about anywhere on your system (preferably under your home directory for a single-user installation). We recommend that you use `git` to clone the EGSnrc repository, but alternatively you may download a compressed image of the EGSnrc directory.

##### Clone the git repository (preferred method)

1. Open a terminal shell
2. Check that git is available on your system: `git --version`
3. Change directory to the desired install location: `cd path/to/your/install/location`
4. Clone the EGSnrc repository: `git clone git@github.com:nrc-cnrc/EGSnrc.git`

##### Download as a zipped archive (alternative method)

1. Download the compressed image [EGSnrc-master.zip](https://github.com/nrc-cnrc/EGSnrc/archive/master.zip)
2. Move the `EGSnrc-master.zip` file to the desired install location
3. Uncompress the archive using the `unzip` command-line tool, or your favorite utility
4. If you want, you can rename the inflated `EGSnrc-master` directory to `EGSnrc` 


### 3. Configure EGSnrc

Once you have the EGSnrc source code on your computer, you must configure EGSnrc for your particular operating system and software environment, using either a configuration GUI or a configuration shell script that prompts you for configuration options on the command-line.

##### Configure using the GUI (easiest method)

##### Configure using the shell script (most flexible method)

1. Open a terminal bash shell
3. For a fresh install, clear existing EGSnrc environment variables: `export HEN_HOUSE= EGS_HOME= EGS_CONFIG=`
2. Go to your EGSnrc directory: `cd path/to/EGSnrc/directory`
4. Launch the configuration script: `./HEN_HOUSE/scripts/configure`
5. Answer prompts and follow instructions rigorously