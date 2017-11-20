---
title: "Dakota Installation on Ubuntu 16.04"
excerpt: "This post shows how to compile Dakota in Ubuntu 16.04"
header:
  overlay_color: "#333"
  teaser: "/assets/images/teaser/compile_dakota.png"
categories:
  - Dakota
tags:
  - Compile
  - Optimization
  - Ubuntu
  - Dakota
last_modified_at: 2017-11-20T17:35
---

[Dakota](https://dakota.sandia.gov/) is a flexible tool which compounds a lot of mathematical and statistical methods. Dakota is extremely useful when we combine it with a simulation procedure such as OpenFoam. 

However, Sandia Lab does not provide a build version for Ubuntu. Also, when I look around some forums, there is no detailed tutorial shows how to do that. Therefore, I write this one to share my way, step by step. I hope this could help someones those are not familar with compiling app in Ubuntu. The build was done for dakota 6.4 but might work with newer versions.

"Update 2017-11-20: This build is work for dakota v6.7"

### 1 Preparation:

#### 1.1  Install some nessesary packages

  ```bash
  ~$ sudo apt-get install gcc g++ gfortran cmake cmake-curses-gui libboost-dev libboost-all-dev libblas-dev liblapack-dev libopenmpi-dev openmpi-bin openmpi-doc xorg-dev libmotif-dev
  ```

​    Explain:

  - GNU 4.8 compilers: gcc g++ gfortran
  - CMake 2.8.12: cmake cmake-curses-gui
  - Boost: libboost-dev libboost-all-dev
  - Linear Algebra: libblas-dev liblapack-dev
  - OpenMPI: libopenmpi-dev openmpi-bin openmpi-doc
  - XWindows: xorg-dev libmotif-dev
  - Python (optional): Python development dependencies (if using direct Python interface: python-dev, and python-numpy if you'd like a NumPy interface.

#### 1.2 Download DAKOTA source code on website.
  
  - At the moment I wrote this tut, I successful compiled the newest version of Dakota (v6.7). So you can download any version you want to use from v6.4 --> 6.7.
  - Create DAKOTA folder and [dowload](https://dakota.sandia.gov/download) the source into it.

#### 1.3  Extract file in terminal.
  
  - Open terminal in DAKOTA folder and run the following code
  ```bash
  $ tar -xzf dakota-<version>-public-src.tar.gz 
  ```
  - Now we have the source code.
#### 1.4 Create and go to dakota-6.4.0 folder

  - From version 6.5, if you make the build and installation in the same folder, error may occur. So, I suggest we should make separated folders for each. In the case you want to install in /usr/local/bin, you can obmit the install folder.

  ```bash
  $ mkdir dakota_build
  $ mkdir dakota_installation
  $ export DAK_BUILD=$HOME/DAKOTA/dakota_build
  $ export DAK_INSTALL=$HOME/DAKOTA/dakota_installation
  $ export DAK_SRC=$HOME/DAKOTA/dakota-<version>-public-src
  $ cd $DAK_BUILD 
  ```
  `- Note: dakota-<version>-public-src is folder where you extract dakota files.`

#### 1.5 Copy file BuildDakotaTemplate.cmake and rename it to BuildDakotaCustom.cmake. You can edit some features if you want, check the content inside for detail.

  ```bash
  ~$ cp $DAK_SRC/cmake/BuildDakotaTemplate.cmake $DAK_SRC/cmake/BuildDakotaCustom.cmake 
  ```

### 2 Building

#### 2.1  Run Cmake
  
  - If you want to install dakota in specific folder, you need to config `-DCMAKE_INSTALL_PREFIX` to folder you want:
  ```bash
  $ ccmake -C $DAK_SRC/cmake/BuildDakotaCustom.cmake $DAK_SRC -DCMAKE_INSTALL_PREFIX=$DAK_INSTALL 
  ```
  - If you want to install dakota in default folder.
  ```bash
   $ ccmake -C $DAK_SRC/cmake/BuildDakotaCustom.cmake $DAK_SRC
  ```


   Note:

   > - Cmake shows a simply GUI and when you enter in ccmake, first press the key "c" to configure the script.
   > - If any error appears, go to the last line to check. If no, press "e" to return the main GUI.
   > - In main GUI, press "t" to toggle some features. Now you can move down and up the cursor. You can turn ON and OFF the features by press Enter.
   > - `Go down, find BUILD_SHARE_LIBS and turn it OFF (by default: it's turned ON). We turn off this since it conflicts with a library in OPENFOAM (libsampling.io).`
   > - You also can move down to check the HAVE_X_GRAPHICS feature ON or OFF. This function shows a graph when u run dakota.
   > - All finish, press "c" again to configure all scripts. If no error appears, you can press "e" to back to the main menu.
   > - Finally press "g" to start generating the configuration.       


#### 2.2 Run make

>(The -j option means we will compile in parallel. In this case I am compiling with 4 processors. You can adjust this option to suit with your hardware)

   ```bash
   ~$ make -j4
   ```

#### 2.3 Install

   ```bash
   ~$ make install                                                                             
   ```

### 3 Path and Test

#### 3.1 Add Path

- ***If you install dakota in your specific folder***, do not forget to add the following environment variables to your *.bashrc* file. Add the following lines at the end of *bashrc* and save

   ```bash
   $ gedit ~/.bashrc
   $ export PATH=$PATH:~/DAKOTA/dakota_installation/bin:~/DAKOTA/dakota_installation/test
   $ export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:~/DAKOTA/dakota_installation/bin:~/DAKOTA/dakota_installation/lib 
   ```
- If you install in default folder, just obmit this step.
#### 3.2 Test build

   ```bash
   ~$ dakota -v
   ```
  If the screen show the version and build date, the job is finished!  You also can follow the steps on [ the Dakota website](https://dakota.sandia.gov/content/test-installation-0) to fully check the installation. 

Congratulation! Now you can use dakota in Ubuntu.
