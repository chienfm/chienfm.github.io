---
title: "Compile Dakota for Ubuntu 16.04"
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
last_modified_at: 2017-10-22T22:37
---
[Dakota](https://dakota.sandia.gov/) is a flexible tool which compounds a lot of mathematical and statistical methods. Dakota is extremely useful when we combine it with a simulation procedure such as OpenFoam. 

However, Sandia Lab does not provide build version for Ubuntu. Also, when I look around some forums, there is no detailed tutorial for Ubuntu 16.04. Therefore, I'm going to write this one to share my way, step by step. I hope you find them useful. 

### 1 Preparation:

1.  Install some nessesary packages

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

2. Create the installation directory ($DAKOTA), and copy DAKOTA source code on it.	       
3.  Extract file in terminal.

  ```bash
  ~$ tar -xzf dakota-6.4.0-public-src.tar.gz 
  ```

4. Create and go to dakota-6.4.0 folder

  ```bash
  ~$ cd DAKOTA
  ~$ mkdir dakota-6.4.0
  ~$ cd dakota-6.4.0 
  ```

5. Copy file BuildDakotaTemplate.cmake and rename it to BuildDakotaCustom.cmake. You can edit some features if you want, check the content inside for detail. 

  ```bash
  ~$ cp ~/DAKOTA/dakota-6.4.0.src/cmake/BuildDakotaTemplate.cmake ~/DAKOTA/dakota-6.4.0.src/cmake/BuildDakotaCustom.cmake 
  ```

### 2 Building

1.  Run Cmake

   ```bash
   ~$ ccmake -C ~/DAKOTA/dakota-6.4.0.src/cmake/BuildDakotaCustom.cmake ~/DAKOTA/dakota-6.4.0.src -DCMAKE_INSTALL_PREFIX=~/DAKOTA/dakota-6.4.0 
   ```

   Note:

   > - Cmake shows a simply GUI and when you enter in ccmake, first press the key "c" to configure the script.
   > - If any error appears, go to the last line to check. If no, press "e" to return the main GUI.
   > - In main GUI, press "t" to toggle some features. Now you can move down and up the cursor. You can turn ON and OFF the features by press Enter.
   > - Go down, find BUILD_SHARE_LIBS and turn it OFF (by default: it's turned ON). We turn off this since it conflicts with a library in OPENFOAM (libsampling.io).
   > - You also can move down to check the HAVE_X_GRAPHICS feature ON or OFF. This function shows a graph when u run dakota.
   > - All finish, press "c" again to configure all scripts. If no error appears, you can press "e" to back to the main menu.
   > - Finally press "g" to start generating the configuration.       

2. Run make (The -j options is to compile in parallel, in this case I am compiling with 4 processors.)

   ```bash
   ~$ make -j4
   ```

3. Install

   ```bash
   ~$ make install                                                                             
   ```

### 3 Adding path

1. When you finish the compilation, do not forget to add the following environment variables to your *.bashrc* file. Add the following lines at the end of *bashrc* and save.  

   ```bash
   ~$ gedit ~/.bashrc
   ~$ export PATH=$PATH:~/DAKOTA/dakota-6.4.0/bin:~/DAKOTA/dakota-6.4.0/test
   ~$ export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:~/DAKOTA/dakota-6.4.0/bin:~/DAKOTA/dakota-6.4.0/lib 
   ```

2. Test build

   ```bash
   ~$ dakota -v
   ```
  If the screen show the version and build date, the job is finished!  You also can follow the steps on [ the Dakota website](https://dakota.sandia.gov/content/test-installation-0) to check the installation. 

Now you can use dakota in Ubuntu. The build was done for dakota 6.4 but might work with newer versions.
